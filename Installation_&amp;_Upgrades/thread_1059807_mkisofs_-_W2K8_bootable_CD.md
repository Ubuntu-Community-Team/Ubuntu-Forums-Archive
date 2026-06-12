---
title: "mkisofs - W2K8 bootable CD"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by vincentb on 2009-02-04
All,

A couple of months ago, I received a DVD for the beta version of Windows server 2008. I do not have this DVD anymore.

Instead of duplicating the DVD (I should really have done that ...), I copied its content on my hard disk. An know I have to test and validate new requirements.

**Option 1 :** I would like to use this directory in order to generate a bootable ISO file from which I will boot to create a virual machine in VMWare. 
Problem: I can generate an ISO file (mkisofs -o name_of_the_iso.iso source_path) but when I boot a VM with that ISO, I get an error (non bootable disk) from VMWare.

I am pretty sure I need additional parameters in the mkisofs command. Can you help as this command seems very complex?

**Option 2:** recreate the DVD based on the content of the directory. I then copied the content of my directory into a DVD. When I boot my PC on this DVD, I get an error message (non system disk??? if I remeber well)

Any suggestion is more than welcome,
Thanks in advance,

Best regards,

Vincent

---

### Post by Neural oD on 2009-02-04
do you have the boot.img file

---

### Post by Neural oD on 2009-02-04
you need to put all the files including the image file into a folder - lets call it win2008, and we'll call the image file win.img - as I'm not too sure what it'll be called! then go to the folder where the win2008 folder is and run this:
mkisofs -b win.img -no-emul-boot -N -l -v -no-iso-translate -relaxed-filenames -o win2008.iso win2008/

you might have to put a -D in after mkisofs - but i'm not too sure - you'll have to play around with it - but i think something like that should work ;)

---

### Post by QueueNut on 2009-07-16
Along similar lines as vincentb's original post -

The difference being I downloaded an ISO image of the operating system.  Don't have the boot.img or boot image file.  How can a bootable DVD be created from just the ISO file?

Thanks much for any pointers.  :confused:

---

### Post by QueueNut on 2009-07-17
Made a little progress, on paper...

The various necessary boot files are inside the ISO file, requiring "disassembly" of the ISO into a temp directory to get at those files.  Not [yet] familiar with what Linux utility will extract files from an ISO image.

---

### Post by QueueNut on 2009-07-17
All right it's all about mounting the ISO file using ISO9660 filesystem, allowing direct copy of files into a directory.  Nice.  All from the CLI (command line).  Better.

As the questions and answer them.  Obviously insane.

'night.

---

