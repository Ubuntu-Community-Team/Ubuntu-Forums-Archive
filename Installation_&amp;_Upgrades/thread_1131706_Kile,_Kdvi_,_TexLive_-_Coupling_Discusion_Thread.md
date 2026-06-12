---
title: "Kile, Kdvi , TexLive - Coupling Discusion Thread"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by neo.patrix on 2009-04-21
Why are Kile , Kdvi and Texlive so tightly coupled? 

There are certain things that I would like to mention. Recently I have 
installed Texlive 2008 from its .iso with Kile compiled from Source Code
I am still struggling with kdvi a bit. Before choosing Texlive 2008, I
was really interested in using MikTex with Kile. But MikTeX still is 
Beta stage for Linux Systems & not really complete. But it is going nice
a nice option to TexLive

1) Not good for people who are really interested in knowing what & where 
   their TexLive Packages are installed. I cannot simply understand which
   Ubuntu Package to install for particular TexLive Package. Lets say I
   simply do not want to install "TexLive - Full" just because I do not
   know xyz.sty & yet do not want to download it form CTAN but manage it
   via Package Manager that shows xyz. 

   I can understand managing all TexLive Packages through aptitude might
   be impractical since CTANs host lot of packages

2) What if I want Kile & simply do not want TexLive but I want to work 
   with MikTex?

3) Previously Kile & Kdvi used to bring in all teTeX Packages , now they
   bring in all TexLive Packages (uninvited). Kdvi depend on package
   texlive-fonts-recommended (ubuntu package), I think. Going deeper in
   dependency tree it brings most of TexLive Packages. 

Is KDVI only for TeX Authoring? What if I just want to view DVI files
without TexLive? What if in future I want Kdvi & Kile from Ubuntu Repo
with MikTeX and do not want a single config file from TexLive because it 
interferes with my MikTex (and cause un-wanted , un-natrual, un-required
REDUNDANCY).

In-short, I request package-manager to look after  Kile,  Kdvi and TexLive
without dependency. Is that possible?


PS : I have nothing against package-manager , really like it taking care 
of stuff, exception just for TexLive

---

### Post by gnwiii on 2009-05-09
Like mail user agents, all package managers suck.  The dependencies need to set so that a user who is not familiar with TeX or linux can get a working system without manually installing extra stuff.  Maybe one day we will have a less sucky package manager that can be adjusted to the user's skill level, preferences, and hardware.  True current dependencies often result in installing a lot of things that the user doesn't need, but disk is cheap and many people find it easier to get money for better hardware than to learn enough so they can optimize their installation.

Unless disk space is really tight, TeX Live from CTAN can coexist with texlive from a distro (just don't select the symbolic links option in the installer).  It is quite easy to create dummy packages to satisfy dependencies in the package manager (because you know the required bits were installed outside the package manager), and less easy to remember to change the dummy package when you add/remove things outside the package manager.

Dvi viewers are problematic because they often need to generate font bitmaps using the TeX metafont system.  Since this means using kpathsea,  a dvi viewer may not work with a different tex system due to changes in the texmf.cnf format, etc.  If you install texlive from CTAN, you should use the dvi viewer from the installation.  This is just one of many reasons to avoid .dvi and use pdf(la)tex if at all possible.  If you embed fonts, the .pdf file can be used with any bug-free viewer, and there are many.

---

### Post by lethalfang on 2009-05-10
Kile is merely a text editor designed for LaTeX. Kile without texlive is useless. Texlive is the LaTeX engine that compiles your .tex files.

---

### Post by Stefan_K on 2009-05-14
> **neo.patrix said:**
> 
What if I want Kile & simply do not want TexLive but I want to work with MikTex? ...
Previously Kile & Kdvi used to bring in all teTeX Packages , now they bring in all TexLive Packages (uninvited). Kdvi depend on package texlive-fonts-recommended (ubuntu package), I think. Going deeper in dependency tree it brings most of TexLive Packages. 
... What if in future I want Kdvi & Kile from Ubuntu Repo
with MikTeX and do not want a single config file from TexLive 


gnwiii has mentioned dummy packages: you could create such packages claiming to provide certain texlive packages. You could use the tool equivs for that purpose. Here's a description with example: [Kile and TeX Live 2008 on Ubuntu Linux]("http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/").

> **lethalfang said:**
> Kile without texlive is useless.
I've installed the newer TeX Live 2008 on my system. Kile dependent on texlive would cause the installation of a lot of texlive2007 packages from the repositories - *that's* useless. I would prefer to remove that dependency of Kile to allow the independent installation of TeX Live 2008, especially because TeX Live 2008 will probably never appear for Ubuntu, we will have to wait for the 2009 version.

Stefan


--
[TeXblog.net]("http://texblog.net")

---

### Post by neo.patrix on 2009-05-26
Advance Users who can tell difference between top-layer editor like Kile and underlying system like Tex System. Also, are advance enough to compile their latex files with "make" command , use Kile only for better management. Anyone wants to install Kile & Tex Scripting , I am quite sure is also aware that Kile is just an editor , without underlying TeX System it is useless. 

[COLOR="Red"]So, Kile is useless without TeX is not a valid reason to force dependecy.[/COLOR] Even if dependency is forced why always get latest Kile but not latest version of TeXLive in Ubuntu Packaging?

---

