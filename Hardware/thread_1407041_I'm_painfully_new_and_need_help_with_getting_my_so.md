---
title: "I'm painfully new and need help with getting my sound running"
date: 2010-02-14
forum: Hardware
---

### Post by ANlMAL on 2010-02-14
Okay background:

I am on a hp dv6000. . .

I am trying to get my sound working but am having some issues (no big surprise here).

I found the resolution to my problem in the Ubuntu Forum hereL

**      [[SOLVED] Realtek released High Definition Audio Drivers for No Sound problem]("http://ubuntuforums.org/showthread.php?t=557031")  **

Of course these is no easy solution for me, i am at the moment borderline hopeless...

Okay, so I have gotten as far as downloading the files from Realtek here:

[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

I have even extracted the file to my desk top and managed to open the readme! :o

This is where I become completely helpless! These are the instructions, any advice on how to actually follow them would bring tears to my eyes. 

> The ALSA driver replaces the OSS/Free driver.  Since version 0.4.0,
ALSA has supported only 2.2 or later kernels. The 2.0 kernels are no
longer supported.

You must compile the kernel with sound support (CONFIG_SOUND on
2.2/2.4 kernels) either as module or built-in.  You do not need to
select any of the other sound modules apart from sound support.

Before installing this driver, it will be helpful to read carefully
the documentation for insmod, modprobe, kmod and for the isapnp
module if you have an ISA PnP soundcard.


Module option name change after 0.9.0rc3
========================================

Note that module option names were changed in 0.9.0rc4. The 'snd_' prefix
was removed. You may use script in utils directory (module-options) to
convert your older /etc/modules.conf to newer one.


Quick install
=============

1) You must have full configured source for the Linux kernel which you
   want to use for the ALSA drivers. Note that ALSA drivers are part
   of the kernel, so there is necessary to resolve all symbol dependencies
   between the used kernel and ALSA driver code. Partly installed kernels
   (for example from distributor makers) can be unuseable for this action.

2) You must turn on sound support (soundcore module).

3) Run './configure' script.
Thanks a lot people!

---

### Post by lidex on 2010-02-14
I'm don't know about that method - scares me a little. I got audio working on my dv7 with an alsa upgrade and adding a couple of lines to alsa-base.conf.

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")
[http://ubuntuforums.org/showthread.php?t=1182587]("http://ubuntuforums.org/showthread.php?t=1182587")

---

### Post by ANlMAL on 2010-02-14
hey thanks very much for your reply! i will check out the links you posted for me, hopefully i can get my sound working! 

out of curiosity, why does the method i posted 'scare you a bit'? is it the messing around with the kernel? 

i only ask because i would really like to develop a semi-proficiency with this type of OS and attendant software so i don't have to be inappropriately touched by microvsoft any more. ;)

---

