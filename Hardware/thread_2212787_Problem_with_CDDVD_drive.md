---
title: "Problem with CD/DVD drive"
date: 2014-03-23
forum: Hardware
---

### Post by christon74 on 2014-03-23
Hello Ubunters :)

I really do not know what's wrong with my CD/DVD drive. If I want to play any film, no problem, films will play. But If I try extracting music tracks using Juicer, then I get the message: 'cannot mount CD' or 'location not supported'. Huh? :confused:

Any suggestion highly welcome. Thanks in advance for all help and trouble. 
Have a nice Sunday. 
chris.

---

### Post by christon74 on 2014-03-23
some more details about the CD/ DVD drive:
Model: HL-DT-ST HL-DT-STDVD-ROM GDRH 10 N
serial number: -
Firmware version; D70D
connection: SCSI
SMART status :not supported
Device: /dev/sr0
Location: Port 2 of PATA Host Adapter

---

### Post by christon74 on 2014-03-23
Hello again fellow ubunters :smile:
problem solved. 
             This is a known bug: [Bug #609020]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/609020").
  Workaround: 
 Install [gvfs-backends]("http://packages.ubuntu.com/gvfs-backends") [[IMG]http://bit.ly/software-small[/IMG]]("http://apt.ubuntu.com/p/gvfs-backends")

[http://askubuntu.com/questions/18724/unable-to-mount-audio-disc](http://askubuntu.com/questions/18724/unable-to-mount-audio-disc)

---

### Post by ajgreeny on 2014-03-23
Is juicer looking for /dev/cdrom instead of /dev/sr0?  Thisd can be a problem sometimes in other applications, but as I am not using juicer I do not know how it's configured.

I use abcde to rip any CDs, which is simple, fast and very configurable.  It is, however, a command-line application, which you may think makes it difficult to use; believe me, it is easy once you have it set up.  I use a config file which I copied from the default version in /etc/abcde.conf with changes to just a few lines, ie removing the comment marks and changing the options:-

```
LAME=lame
LAMEOPTS="--alt-preset standard"
CDROM=/dev/sr0
OUTPUTDIR=/home/user/abcde
OUTPUTTYPE=mp3


```
The LAMEOPTS I used is from the **man lame** output which shows
```
--preset standard
              This preset should generally be transparent to most people on most music and is already quite  high  in
              quality.
```
but you could use whatever quality you want.

---

### Post by christon74 on 2014-03-24
Apologies for not coming back to you any sooner ajgreeny and thanks for the tip. Anyway the 'gvfs-backends' does the trick and now everything is working just fine: i can extract music using sound juicer.

---

