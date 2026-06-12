---
title: "System fonts all boxes squares rectangles invalid need to customize so i can read"
date: 2008-09-16
forum: General Help
---

### Post by dwreck86 on 2008-09-16
xfonts-scalable returns an error

usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts. See update-fonts-dir( for more information.
Options:
-h, --help display this usage message and exit
dpkg: error processing xfonts-scalable (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
xfonts-scalable
E: Sub-process /usr/bin/dpkg returned an error code (1)

not sure what this is about.. also, my system fonts ALL SHOW BOXES after an update and i have a feeling this has something to do with it. i dont care if i upgrade, i just want to be able to read whats happening. is there a way to change the fonts to something i can read via the terminal? i see people having issues with this all over the internet, with no resolution..


saw this posted somewhere online thought id post it here, im not sure how to do this lol

I had the same problem, while upgrading from edgy to feisty.
Then I upgraded xfonts-utils first (it contains update-fonts-dir).
This new update-fonts-dir accepts the -x11layout option.

that helped that person out... but im not sure how to do it...

---

