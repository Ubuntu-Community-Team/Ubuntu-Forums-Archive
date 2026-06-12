---
title: "Soundcard not detected and so not working"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by oden08 on 2005-04-22
Upon install my sound isn't working. I know the module which I need to be using (snd-nm256, because I have a NeoMagic 256) but don't know where to go from there. I was reading a doc which referenced an "ALSA-Configuration.txt" file but I don't have that on my PC and can't find it anywhere.  Can someone help me with progressing (and if possible, tell me where I could have found it? --No use in knowing how to get home if you don't know where you took the wrong turn for next time, right?)?  Thanks.

---

### Post by heimo on 2005-04-22
Have you tried loading that module? Try *modprobe snd-nm256*
*(*this command should give no warnings if successul)
 
You could also post the output of command line command *lspci*
 
Check if you have /dev/dsp present: *ls -l /dev/dsp*
 
And also you could post the output of 
```
 lsmod | grep snd
``` 
 
While doing all this, keep one terminal window open and run
```
 tail -f /var/log/messages
``` 
to see if there's something interesting.

---

### Post by oden08 on 2005-04-22
I am attaching the information that you requested.  I don't have /dev/dsp present, I guess this is a problem.  What is dsp?

geek@ubuntu-JT:~ $ modprobe snd-nm256
geek@ubuntu-JT:~ $ ls -l /dev/dsp
ls: /dev/dsp: No such file or directory
geek@ubuntu-JT:~ $ ls /dev
agpgart  md1   mem     shm      tty24  tty46  ttyS1   ttyS31  ttyS53
cdrom    md10  null    snd      tty25  tty47  ttyS10  ttyS32  ttyS6
console  md11  port    sndstat  tty26  tty48  ttyS11  ttyS33  ttyS7
core     md12  psaux   stderr   tty27  tty49  ttyS12  ttyS34  ttyS8
dvd      md13  ptmx    stdin    tty28  tty5   ttyS13  ttyS35  ttyS9
evms     md14  pts     stdout   tty29  tty50  ttyS14  ttyS36  urandom
fd       md15  ram0    tty      tty3   tty51  ttyS15  ttyS37  vcs
fd0      md16  ram1    tty0     tty30  tty52  ttyS16  ttyS38  vcs1
full     md17  ram10   tty1     tty31  tty53  ttyS17  ttyS39  vcs2
hda      md18  ram11   tty10    tty32  tty54  ttyS18  ttyS4   vcs3
hda1     md19  ram12   tty11    tty33  tty55  ttyS19  ttyS40  vcs4
hda2     md2   ram13   tty12    tty34  tty56  ttyS2   ttyS41  vcs5
hda5     md20  ram14   tty13    tty35  tty57  ttyS20  ttyS42  vcs6
hdc      md21  ram15   tty14    tty36  tty58  ttyS21  ttyS43  vcs7
initctl  md22  ram2    tty15    tty37  tty59  ttyS22  ttyS44  vcsa
input    md23  ram3    tty16    tty38  tty6   ttyS23  ttyS45  vcsa1
kmem     md24  ram4    tty17    tty39  tty60  ttyS24  ttyS46  vcsa2
kmsg     md3   ram5    tty18    tty4   tty61  ttyS25  ttyS47  vcsa3
log      md4   ram6    tty19    tty40  tty62  ttyS26  ttyS48  vcsa4
lp0      md5   ram7    tty2     tty41  tty63  ttyS27  ttyS49  vcsa5
lvm      md6   ram8    tty20    tty42  tty7   ttyS28  ttyS5   vcsa6
MAKEDEV  md7   ram9    tty21    tty43  tty8   ttyS29  ttyS50  vcsa7
mapper   md8   random  tty22    tty44  tty9   ttyS3   ttyS51  xconsole
md0      md9   rtc     tty23    tty45  ttyS0  ttyS30  ttyS52  zero
geek@ubuntu-JT:~ $ lsmod | grep snd
snd_nm256              69032  0
snd_ac97_codec         59268  1 snd_nm256
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_nm256,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  6 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
geek@ubuntu-JT:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1211
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)
geek@ubuntu-JT:~ $ ls mod | grep snd
ls: mod: No such file or directory
geek@ubuntu-JT:~ $ lsmod | grep snd
snd_nm256              69032  0
snd_ac97_codec         59268  1 snd_nm256
snd_pcm_oss            48168  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                85540  2 snd_nm256,snd_pcm_oss
snd_page_alloc         11144  1 snd_pcm
snd_timer              23172  1 snd_pcm
snd                    50660  6 snd_nm256,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
geek@ubuntu-JT:~ $

---

### Post by heimo on 2005-04-22
The file you were looking for is probably this one:
[http://cvs.sourceforge.net/viewcvs.py/alsa/alsa-kernel/Documentation/ALSA-Configuration.txt?rev=1.70&view=markup]("http://cvs.sourceforge.net/viewcvs.py/alsa/alsa-kernel/Documentation/ALSA-Configuration.txt?rev=1.70&view=markup")
 
Hmm.. I thought that I'd see that module (snd_nm256) missing in lsmod (lists the modules which have been loaded), but there it was. I think the /dev/dsp is the device for your soundcard.
 
>  
    Note: The NM256 chip can be linked internally with non-AC97
    codecs.  This driver supports only the AC97 codec, and won't work
    with machines with other (most likely CS423x or OPL3SAx) chips,
    even though the device is detected in lspci.  In such a case, try
    other drivers, e.g. snd-cs4232 or snd-opl3sa2.  Some has ISA-PnP
    but some doesn't have ISA PnP.  You'll need to speicfy isapnp=0
    and proper hardware parameters in the case without ISA PnP.

    Note: This driver is really crappy.  It's a porting from the
    OSS driver, which is a result of black-magic reverse engineering.
    The detection of codec will fail if the driver is loaded *after*
    X-server as described above.  You might be able to force to load
    the module, but it may result in hang-up.   Hence, make sure that
    you load this module *before* X if you encounter this kind of
    problem.

 
 
Check what you have in /etc/modules and if snd_nm256 is not there, add it to the top of the list... And cross your fingers, as in worst case your computer will have hard time booting. Most of the time this doesn't prevent booting, but it may.
 
Now, reboot - and let's hope for the best. Seems like this module doesn't want to be autodetected and loaded on demand. That's... That's incredibly bad driver.
 
If that fails, try the other modules mentioned in the quotation abowe.

---

### Post by oden08 on 2005-04-25
Have tried the other modules but still no luck.  I am at a loss at this point.  I wonder if there is another application other than ALSA that I can try and work with since I from what I can understand it is a "crappy" module.  Anyone have any ideas?  Suggestions??  Thanks.

---

