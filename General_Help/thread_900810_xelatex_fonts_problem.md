---
title: "xelatex fonts problem"
date: 2008-08-25
forum: General Help
---

### Post by nitro_n2o on 2008-08-25
Hi all,

I'm trying to compile a document using xelatex with the fontspec package 
and I keep getting the error 

Metric (TFM) file or installed font not found.

Even though fc-list shows the name of the font

I have everything installed from the texlive package

Any ideas? thx

---

### Post by Orion8 on 2009-02-01
I'm having the same problem and would appreciate any insight. I have the open type font I want to use installed system wide in /usr/share/fonts as well as in /usr/share/texmf/fonts/opentype.

Thanks.

[Edit: I am not sure what was wrong but my problem is fixed. I made a fresh copy of the opentype font folders I wanted to use from the Adobe CD to my desktop.  The permissions were wrong so I fired up Nautilus in sudo mode and changed them, making sure to apply the changes to the files in the folders.  I then copied them (still in sudo nautilus) to /urs/share/fonts/opentype.  I did not change the folder names to lower case or anything, left them as is (eg "Minion Pro").  Xelatex now works fine with the font name in the fontspec call matching the folder name.  XeLatex did not require the fonts to be re-cached either.  I think the problem might have been a permissions thing but I am not 100% on that.  Anyway, maybe this'll help somebody else out!]

---

### Post by bopomofo on 2009-04-08
> **Orion8 said:**
> I'm having the same problem and would appreciate any insight. I have the open type font I want to use installed system wide in /usr/share/fonts as well as in /usr/share/texmf/fonts/opentype.

I've found the following technique works for OpenType fonts under XeTeX.

Put the font folder containing your .otf files in your home directory: ~/.fonts/ (Sorry, I haven't tried system-wide installation, but that should work too)

Rebuild your font cache: sudo fc-cache -f -v

Next, don't use the Folder name of the font (that has never worked for me). Instead, use the name of the individual .otf file.

For example, the folder for JansonText might contain the files JansonTextLTStd-BoldItalic.otf,  JansonTextLTStd-Italic.otf, JansonTextLTStd-Bold.otf and JansonTextLTStd-Roman.otf

If you want to set JansonText as your roman font, try:
```

\setromanfont{JansonTextLTStd-Roman}
```

If you want to use the complementary italic, then try:
```

\setromanfont[ItalicFont={JansonTextLTStd-Italic}]{JansonTextLTStd-Roman}
```

For Minion (which has many different weights), I would write
```

\setromanfont[ItalicFont={MinionPro-It}]{MinionPro-Regular}
```

Where the corresponding filenames are MinionPro-It.otf and MinionPro-Regular.otf

Consulting the output of fc-list has unfortunately never helped me use a font in XeTeX, but only confirm whether or not it being recognized in my font cache.

---

### Post by Narayana on 2009-05-04
I am facing the same problem as above.  Need to try the ~/.fonts  solution offered for open type fonts, but i have already tried the trick with no result, with true type fonts.

---

### Post by Garzo on 2009-05-06
XeTeX uses quite fonts in a straightforward manner. It really is easy and logical. XeTeX can use any font installed on your system — either in /usr/share/fonts/ or ~/.fonts/. If you want a GUI to make sure a font file is installed, use KFontView: it can install any font and update the font cache. Otherwise, follow the instructions above by putting the font file in either of those directories and manually updating the cache.

There are two ways to use fonts in XeTeX: the plain way, and using fontspec.sty. The Plain XeTeX way uses the format:

[FONT="Fixedsys"]\font\tenrm="Times New Roman" at 10pt[/FONT]

This defines the control sequence [FONT="Fixedsys"]\tenrm[/FONT] for switching to Times New Roman at 10pt.

If you use fontspec.sty (type [FONT="Fixedsys"]texdoc fontspec &[/FONT] in a terminal to read the documentation), the format is:

[FONT="Fixedsys"]\fontspec{Times New Roman}[/FONT]

This has the advantage of allowing you to choose options, as:

[FONT="Fixedsys"]\fontspec[Scale=MatchLowercase, Script=Vietnamese]{Times New Roman}[/FONT]

What's probably more useful than the [FONT="Fixedsys"]\fontspec[/FONT] command, are these:

[FONT="Fixedsys"]\setmainfont[Mapping=tex-text]{Times New Roman}
\setsansfont{Helvetica}
\setmonofont[Scale=MatchLowercase]{Monospace}
\newfontfamily\hebrewfont[Script=Hebrew]{Ezra SIL}[/FONT]

I hope it's straightforward what that code does; you can then use normal font changing commands like [FONT="Fixedsys"]\sffamily[/FONT], or new ones like [FONT="Fixedsys"]\hebrewfont[/FONT], to change font.

About font names, use the natural, human-readable name of the font. This is the name shown as [FONT="Fixedsys"]**Name:** MPH 2B Damase[/FONT] in Font Viewer, or at the top of KFontView. Really do not bother to call the italic or bold version unless you have to (which is usually {Times New Roman-Italic} with a hyphen), as [FONT="Fixedsys"]\newfontfamily[/FONT] etc. calls all the shapes and weights.

Top tip: [FONT="Fixedsys"]\usepackage{xltxtra}[/FONT] usefully calls fontspec.sty and xunicode.sty with it, so use that to simplify your syntax.

---

### Post by noran on 2010-05-19
Hello, I'm having the same problem. This is the first time I try to use custom fonts in LaTeX. I installed XeTeX and configured LyX to work with it (it works fine without any custom fonts so far).

I want to use Adobe's Chaparral Pro. I put the fonts everywhere:
```
/usr/share/fonts/
/usr/share/texmf/fonts/opentype
~/.fonts/
```

And I updated the cache. The error appears when I put the line ```
\usepackage{fontspec}
``` even before I try to use any custom fonts (I get errors that the default LM fonts are unloadable). When I do try to use the custom font I get more "unloadable" errors.

Appreciate your help,

---

### Post by noran on 2010-05-19
I figured out where the problem is, but I don't really know what to do about it.

I viewed the LyX source and found that LyX uses two packages:
```
\usepackage[T1]{fontenc}
\usepackage[latin9]{inputenc}
```
I exported the LaTeX code, removed these two lines and called xelatex from the terminal. It worked fine.

Is there a way to stop LyX from producing these two lines? I cannot export my entire masters thesis to LaTeX code every time I want to view the output.

---

### Post by Anaphylaxis on 2010-12-30
> **bopomofo said:**
> I've found the following technique works for OpenType fonts under XeTeX.

Put the font folder containing your .otf files in your home directory: ~/.fonts/ (Sorry, I haven't tried system-wide installation, but that should work too)

Rebuild your font cache: sudo fc-cache -f -v

Next, don't use the Folder name of the font (that has never worked for me). Instead, use the name of the individual .otf file.

For example, the folder for JansonText might contain the files JansonTextLTStd-BoldItalic.otf,  JansonTextLTStd-Italic.otf, JansonTextLTStd-Bold.otf and JansonTextLTStd-Roman.otf

If you want to set JansonText as your roman font, try:
```

\setromanfont{JansonTextLTStd-Roman}
```

If you want to use the complementary italic, then try:
```

\setromanfont[ItalicFont={JansonTextLTStd-Italic}]{JansonTextLTStd-Roman}
```

For Minion (which has many different weights), I would write
```

\setromanfont[ItalicFont={MinionPro-It}]{MinionPro-Regular}
```

Where the corresponding filenames are MinionPro-It.otf and MinionPro-Regular.otf

Consulting the output of fc-list has unfortunately never helped me use a font in XeTeX, but only confirm whether or not it being recognized in my font cache.

Thanks. This worked perfectly for me as well.

---

