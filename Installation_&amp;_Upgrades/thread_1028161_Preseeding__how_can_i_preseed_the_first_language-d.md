---
title: "Preseeding : how can i preseed the first language-dialogue with kernel params"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by gencaslan on 2009-01-02
Hello, 

i try to use preeseeding and everything works fine after 3 days of work but one thing. 

i can't preseed away the first language-dialog after booting from installation-cd. has anybody an idea how to jump over the language-selection-dialog. 

i think it has to be in the isolinux.cfg file as a kernel param. 

i tried a few params but none of them worked. 

e.g. my first lines before label-definition

> DEFAULT myLabel
GFXBOOT bootlogo
APPEND debian-installer/locale=en_US console-setup/layoutcode=de initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet -- 
LABELDEFINITIONS
...
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
...


for now my solution is tu use the non-graphic version with these lines 

> DEFAULT myLabel
#GFXBOOT bootlogo
LABELDEFINITIONS
...
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
...


then the first language-selection-dialog does not appear.


Is there a way to use the GFXBOOT version and preseed away the dialog. Any Ideas ? 

Thanks

---

### Post by gsegree on 2009-01-15
In the text.cfg/isolinux.cfg add the following

label my-install
  menu label ^My Install
  kernel /install/vmlinuz
  append locale=en_US console-setup/layoutcode=us file=/cdrom/preseed/preseed.seed initrd=/install/initrd.gz quiet --
l

---

### Post by rakslice on 2009-11-03
I'm trying to create a custom 8.04 server x64 install CD.  To get around that first language menu before you select a boot choice, I ended up creating a custom gfxboot data file (a replacement for isolinux/bootlogo from the original cd), with the call that shows the language selection menu commented out.

Here's what you'll need to do, as root, in more detail:

[LIST=1]
[*]Install the gfxboot package to get the tools to build the gfxboot.
[*]Get a copy of the standard ubuntu gfxboot theme. It's in the gfxboot-theme-ubuntu package, but the binary package is missing the po/bootloader.pot file, so you'll want to get the source package or just grab a copy of the source from launchpad.
[*]In your gfxboot-theme-ubuntu directory, there's a code file called common.inc. Open it in your choice of text editor.
[*]Find the line that calls panel.lang ('lang.displayed not { panel.lang } if'), and comment it out by inserting a % at the beginning of the line. Save and exit.
[*]Go into the directory po, and do a make.  This will create the text.inc file.
[*]Go back up to your gfxboot-theme-ubuntu directory, and use mkbootmsg to build your new gfxboot file from the modified source:
mkbootmsg -O -c boot.config <your gfxboot filename>
[*]Now, replace the previous gfxboot file with your new one. Since my install is an isolinux install CD, I put my replacement gfxboot file in the isolinux directory of my CD template, and modified the isolinux.cfg so that the GFXBOOT line referred to my file rather than bootlogo.
[/LIST]
Hopefully I didn't miss anything there.

---

### Post by sojou on 2012-03-23
I know it is an old thread. Thanks rakslice. Works perfectly.

---

### Post by nothingspecial on 2012-03-23
> **sojou said:**
> I know it is an old thread.

It is and so it must me closed.

---

