---
title: "Texlive, Beamer and Kile problems in dependency"
date: 2008-09-23
forum: General Help
---

### Post by somesh.roy on 2008-09-23
Just after getting Hardy in my system, I had installed kile and it worked just fine. Recently I needed the document class BEAMER so I downloaded the package from sourceforge. Followed the instructions at [http://www.ctan.org/pub/tex-archive/installationadvice/](http://www.ctan.org/pub/tex-archive/installationadvice/) Then I followed the instruction in the *beameruserguide.pdf*, which came with the beamer package and ran
> $ sudo apt-get install latex-beamer
It showed it needed to remove few packages (I didn't pay much attention to the names, but they were something like libperl...), I did YES. It did install beamer. But still kile/emacs couldn't access beamer. Then I extracted beamer, xcolor and pgf to *$TEXMF/tex/latex/* directory and did <texhash> couple of times. Then while compiling a tex file with beamer emacs showed this error:
> "I can't find the format file `latex.fmt'!"
Then using synaptic I removed kile and reinstalled couple of texlive packages. And while doing this I got dependency error:
 > E: texlive-base-bin: subprocess post-installation script returned error exit status 1
 E: texlive-base: dependency problems - leaving unconfigured
 E: texlive-extra-utils: dependency problems - leaving unconfigured
 E: texlive-fonts-recommended: dependency problems - leaving unconfigured
 E: texlive-latex-base: dependency problems - leaving unconfigured
 E: texlive-latex-recommended: dependency problems - leaving unconfigured
 E: texlive-math-extra: dependency problems - leaving unconfigured

I then tried apt-get with this
> sudo apt-get -f build-dep texlive-base texlive-base-bin texlive-latex-base kile texlive-fonts-recommended texlive-latex-recommended texlive texlive-extra-utils texlive-math-extra
and got broken dependency error again.

Though kile seems to work with usual latex files (not with beamer).
But I would like to do clean installation of texlive (with beamer) and kile.
What should I do?

I forgot to add one more point, first time I did <apt-get -f build-dep> it added a lot of new packages like libperl and some more (which seemed to me matches with the packages removed while doing <apt-get install latex-beamer> first time)

The output of apt-get - here it goes:

> somesh@CreatiVision:$ sudo apt-get -f build-dep texlive-base texlive-base-bin texlive-latex-base kile texlive-fonts-recommended texlive-latex-recommended texlive texlive-extra-utils texlive-math-extra
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Setting up texlive-base-bin (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
 This may take some time...
fmtutil-sys failed. Output has been stored in
/tmp/fmtutil.UTT16171
Please include this file if you report a bug.

dpkg: error processing texlive-base-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-base-bin (>= 2007-13); however:
  Package texlive-base-bin is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kile:
 kile depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing kile (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2007-11); however:
  Package texlive-latex-recommended is not configured yet.
 texlive depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-base (>= 2007-11); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-math-extra:
 texlive-math-extra depends on texlive-fonts-recommended (>= 2007-11); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive-math-extra depends on texlive-latex-base (>= 2007-11); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-math-extra (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 texlive-base-bin
 texlive-base
 texlive-latex-base
 kile
 texlive-fonts-recommended
 texlive-latex-recommended
 texlive
 texlive-extra-utils
 texlive-math-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

The /tmp/fmtutil.UTT16171 file says:
> "fmtutil: config file `fmtutil.cnf' not found."

---

