---
title: "[SOLVED] get short description of package like synaptic shows"
date: 2008-11-27
forum: General Help
---

### Post by jerremy-tamlin on 2008-11-27
Hi all,

I'm trying to find all the applications that I've installed but don't actually use. I'm not trying to find orphaned packages but rather the packages that are the top level of applications I myself interact with. Unfortunately I haven't kept my system very tidy there are a lot more applications installed than are shown in the applications menu.

Does anyone know how I can generate a list with short descriptions of all the 'application' packages installed?


The strategy I've thought to try is to make a list of /usr/bin and process this list through dpkg-query or something to generate a short description of each tool.
There are lots of binary files (tools) in there that aren't named exactly like the package they belong to but it's a start.

Unfortunately dpkg-query doesn't have a 'short description' variable see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=427945](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=427945)

There must be a way to generate such a short description because synaptic does it. Does anyone know how it does?

Thanks in advance for your help and please feel free to tell me a better way if there is one.

Cheers:)

---

### Post by editrix on 2008-11-30
Synaptic is just a frontend to apt. I know you can search packages with apt, get the descriptions, and pipe the output to a file. But I don't know how :-(

try ```
man apt-cache
``` in the terminal.

And if you can understand man pages, you're smarter than I am. If you can't, at least it's a place to start.

---

### Post by jerremy-tamlin on 2008-12-22
[B]I stumbled upon the answer!
[/B]
```
dpkg-query --show --showformat '${description}\n' *package-name* | grep -v "^ "
```

[COLOR="Blue"]dpkg-query --show --showformat '${description}\n' *package-name*[/COLOR] shows the package description nicely formatted
```
$ dpkg-query --show --showformat '${description}\n' audacity
A fast, cross-platform audio editor
 Audacity is a multi-track audio editor for Linux/Unix, MacOS and
 Windows.  It is designed for easy recording, playing and editing of
 digital audio.  Audacity features digital effects and spectrum
 analysis tools.  Editing is very fast and provides unlimited
 undo/redo.
 .
 Supported file formats include Ogg Vorbis, MP3, WAV, AIFF, and AU.
 .
 For more information, see http://audacity.sourceforge.net/.
```

And I noticed that the first line of this output is a nice one line description and is also THE ONLY LINE NOT INDENTED WITH A SPACE!

So [COLOR="Blue"][FONT="Courier New"]grep -v "^ "[/FONT][/COLOR] will give me just this line!
```
$ dpkg-query --show --showformat '${description}\n' audacity | grep -v "^ "
A fast, cross-platform audio editor

```

Bingo! :P

---

