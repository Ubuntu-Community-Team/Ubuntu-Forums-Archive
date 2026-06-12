---
title: "Tamil fonts on Ubuntu"
date: 2005-12-04
forum: General Help
---

### Post by ns80 on 2005-12-04
I have been trying to make this Indic font work for the past 2 weeks, but still no success. The worst part is, I am getting the font rendered correctly in bold (title bar and tab title in the screenshot), but does'nt render correctly in regular :mad: .

Screenshot: [http://img465.imageshack.us/my.php?image=tamilfont24dk.png](http://img465.imageshack.us/my.php?image=tamilfont24dk.png)

So what I did so far: add all .ttf's from my windows fonts directory and then run

```
chown root.root *.ttf
fc-cache
```

in the directory where I put all these new fonts. Yeah ofcourse I did run mkfontdir too. I read from a blog that ttf-freefont does'nt allow Indic fonts to be rendered properly, so I uninstalled that. There was little change, but still the font does'nt look good in regular mode.

Any suggestions ?

---

### Post by desiman on 2006-07-16
hi ,
 i have the same problem as you.
did you solve the problem ? i have not figured it out ?
also why sites like dinamalar.com not displayed properly in ubuntu or any linux distro ?
i installed webcore-fonts of windows in ubuntu . still no luck,

thanks

---

### Post by swamytk on 2006-07-18
> **desiman said:**
> hi ,
 i have the same problem as you.
did you solve the problem ? i have not figured it out ?
also why sites like dinamalar.com not displayed properly in ubuntu or any linux distro ?
i installed webcore-fonts of windows in ubuntu . still no luck,

thanks

Have you installed pango library? try installing it if not? I think it should be available by default. Pango library takes care of rendering CTL (Complext Text Layout) fonts like Tamil.
If you are able to see the text properly in gedit means, the problem is most likely in firefox. If firefox is not built with default pango enabled, you will have this problem. You can try as suggested by this blog post: [http://cutecomputer.wordpress.com/2005/12/01/complex-script-font-rendering-in-simplymepis-34-1-rc1/](http://cutecomputer.wordpress.com/2005/12/01/complex-script-font-rendering-in-simplymepis-34-1-rc1/)

---

### Post by bhuvan72 on 2006-11-10
Hello folks,

I am a newbie and I am trying to get tamil fonts displayed in popular tamil news web pages like...

[www.dinamalar.com](www.dinamalar.com)
[www.tamilvu.org](www.tamilvu.org)
[www.kumudham.com](www.kumudham.com) etc.

Most of them provide a set of True type fonts. I have copied them in the fonts folder and have run fc-config, I do see them listed in StarOffice editor, but I am not able to type in tamil.

Viewing the web pages also shows only symbols instead of tamil chars.

Any help would be greatly appreciated.

Thanks,
Bhuvan.

---

### Post by shyamsundarc on 2007-07-15
hi!!!!

   it will be a nice idea to install tamil fonts and use them for reading the web pages.
   but if you need to post , you actually dont need to get this fonts installed and get accusomed with the new keyboard layout 
     one such tool , which ii came across recenty on net and onw that has helped me a lot recently in posting stuff n all is [http://quillpad.in/tamil](http://quillpad.in/tamil) 
    have a look at it, this will definitely help ones who want to mail quickly in native scripts 

   &#2951;&#2969;&#3021;&#2965;&#3015; &#2997;&#3006; &#2949;&#2996;&#2965;&#3007;&#2991;&#3015;  
&#2951;&#2980;&#3009; &#2980;&#3006;&#2985;&#3021; &#2953;&#2994;&#2965;&#2980;&#3021;&#2980;&#3016; &#2970;&#3009;&#2980;&#3021;&#2980; &#2997;&#3016;&#2965;&#3021;&#2965;&#3007;&#2993;&#2980;&#3009;

---

### Post by ns80 on 2007-07-25
Hmm...its been almost 2 years since I started this thread. I think the problem was because of pango. 'cos in my current distro (Gentoo) installs firefox with pango by default.

I downloaded the [ttf-tamil-fonts source package from Debian]("http://ftp.debian.org/debian/pool/main/t/ttf-indic-fonts/ttf-indic-fonts_0.4.9.tar.gz") used [this guide]("http://aamachu-gnu-explore.blogspot.com/2006/06/fonts-in-gnulinux.html"). Am able to see tamil fonts, although they look a little packed.

---

### Post by ram666 on 2007-11-06
useful tamil font sites 

[www.tamilspace.co.uk](www.tamilspace.co.uk)
[www.suratha.com](www.suratha.com)
[www.jaffnalibrary.com](www.jaffnalibrary.com)
[www.dosai.com](www.dosai.com)

---

### Post by kmashraf on 2008-05-08
[http://thatstamil.oneindia.in/common/unicode/help.html](http://thatstamil.oneindia.in/common/unicode/help.html)

"For Linux Operating System:

Copy one of the Tamil fonts file from Tamil Fonts(but we recommend Lohit-Tamil font) to .fonts directory in the user's home directory. If .fonts directory does not exist in the home directory, please create it. Finally run the command 'fc-cache' from the command prompt.

It is very important to restart the browser, only then you will be able to read the content in Tamil."

use the links in the site to get a hold of the tamil fonts if you need to.

This helped me solve my viewing websites such as dinamalar.com and vikatan.com popular tamil news and magazine sites

---

