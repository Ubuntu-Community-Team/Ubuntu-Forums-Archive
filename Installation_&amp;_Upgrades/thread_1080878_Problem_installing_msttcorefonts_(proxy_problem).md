---
title: "Problem installing msttcorefonts (proxy problem)"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by loyloy on 2009-02-25
Hi,
At work the proxy server does not let me to download files with extension 'exe' ( in addition to many other types of files ) 

so I was trying to install msttcorefonts  and it needed to download 
./andale32.exe . which obviously was blocked my my work 

so the install could not proceed . but it kept trying for long and in furstration i did the evil "control+C" and it aborted

now the problem is whenever i use apt-get to install something at the end i get 

> etting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--10:57:36--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving proxy.*******... failed: Name or service not known.
--10:57:36--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving proxy.*****... failed: Name or service not known.
--10:57:36--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving proxy.******... failed: Name or service not known.
--10:57:36--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving proxy.******... failed: Name or service not known.
--10:57:37--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'

this even when i am using my home connection and i unset the system proxy. 
I am now not even keen on the msttcorefonts . removing it completely using synaptic did not help either. 
I presume in some way my dpkg status is corrupt .. how to solve this annoyance ( my computer seems to be working fine otherwise ) 
Thanks

---

### Post by bazzer on 2009-03-13
When you're at home you could try:
```
sudo apt-get install -f
```
:)

---

