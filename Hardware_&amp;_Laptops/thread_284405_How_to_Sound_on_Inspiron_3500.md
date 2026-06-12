---
title: "How to: Sound on Inspiron 3500"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by Pianoman72 on 2006-10-25
I haven't found any instructions on how to get ALSA sound working in linux on the Dell Inspiron 3500.  Even though there is a nm256 ALSA driver, it is not a good match for our machines.  Who knows what Neomagic-Dell did specific to the 3500, but they are not going to help anytime soon.

Here is the solution: Blacklist other drivers and force-load the SND-SB8 ALSA driver.  It works surprisingly well.

First, in the BIOS - I have the soundcard set to AUTO.  I had been experimenting with manual settings but somehow they would get changed from my selections.

no ac97 is found!
force_ac97=1

I used to see the above message at boot.  Here is my modprobe.conf.

NOTE TO BEGINNERS:  You might need to create a modprobe.conf file (it should be in the /etc directory).

blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8


------

That should get you sound.  Even opl3 MIDI works with xplaymidi.

Anyway, hope this helps a few people out.  I started a new thread because there are just so many threads with no solutions regarding this.

---

### Post by martyrwear on 2006-11-16
Pianoman
I experienced the same problem with my Dell. I gave up after much inconclusive actions upon my part.  Then, I installed Win 2000 and sold it.  However, there is a company that sells the driver. I can not think of the name of it right now, but they have a trial version you can d/l for free.  
BTW - The 3500 has the M/B as the HP Omnibook 4100, 4150; Quantex TS30T and Systemax TS30T.  The video and sound are slightly different in the Dell vs HP, but if someone has a driver that makes any of those work... it might just work for them all.

---

### Post by walzi on 2007-05-04
Thank you very much for this guide. It worked for me in **Ubuntu Feisty** with two minor changes:

Instead of creating the /etc/modprobe.conf file you just have to add a file in /etc/modprobe.d (all files in this directory are read by modprobe) and instead of ```
blacklist snd-nm256
``` I did ```
alias snd-nm256 snd-sb8
```

---

### Post by ahrojm on 2007-08-04
Thank you. This worked for me too. Newbies like me need to know how to get the permission to write in the system's directories. If you are not the owner of the root directory, you cannot create a file in modprobe.d directory or any other directory but your own. I got out of that problem using the UNIX command Chmod 777 on the root. But that leaves the entire system unprotected. So, I thought of protecting myself using the chmod 700 command...and locked myself out of my own laptop! There should be a better way of doing things... You live, you learn.

---

### Post by ahrojm on 2007-08-05
Your solution worked fine the first time around: I created a file in modprobe.d, rebooted and got sound. Then I had to reinstall Ubuntu 7.04 anew. I recreated the same file in modprobe.d. Rebooted.
No sound this time. Any idea someone? Many thanks.

---

### Post by Michael Longval on 2007-12-02
OMG!!!!!!

***_[SIZE="5"]Sound on Dell Inspiron 3500[/SIZE]_*** 

It Works!!!

Yes it's true!!!!!!!!

All hail Pianoman72!!!!

I've been trying this on and off for 2 YEARS ..... never got it working I can hardly believe it

Just to reiiterate what I understood and did running Xubuntu (Dapper ?):

1) In the BIOS set soundcard to AUTO

2) I deleted /etc/modprobe.d/alsa-base  (actually I MOVED it to a safe place just in case)

2b) I deleted the "blacklist sb" line from /etc/modprobe.d/blacklist-oss file

3) I created  /etc/modprobe.d/inspiron3500snd

4) File **/etc/modprobe.d/inspiron3500snd** is  composed of the stanzas posted by Pianoman72:

```
blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8
```

The last 2 lines are rather complex.  So it might be a good idea to cut and paste.

5) VERY IMPORTANT:  For me at least, the above solution only works if I manually reload the snd-sb8 module.  So I added a line to the /etc/modules file.  The stanza that I added is : 

snd-sb8 

Now the module loads automagically at boot time!

Anyway .... can't believe it after 2 years.... this old Dell 3500 is a clunker, but I just couldn't throw it out, only the sound wouldn't work.
I use it in my garage of all places... the sound can NOW pump mp3 from my server to the old stereo there.....

Well many thanks to you Pianoman72!!!!!

Michael Longval

> **Pianoman72 said:**
> I haven't found any instructions on how to get ALSA sound working in linux on the Dell Inspiron 3500.  Even though there is a nm256 ALSA driver, it is not a good match for our machines.  Who knows what Neomagic-Dell did specific to the 3500, but they are not going to help anytime soon.

Here is the solution: Blacklist other drivers and force-load the SND-SB8 ALSA driver.  It works surprisingly well.

First, in the BIOS - I have the soundcard set to AUTO.  I had been experimenting with manual settings but somehow they would get changed from my selections.

no ac97 is found!
force_ac97=1

I used to see the above message at boot.  Here is my modprobe.conf.

NOTE TO BEGINNERS:  You might need to create a modprobe.conf file (it should be in the /etc directory).

blacklist snd-opl3sa2
blacklist snd-nm256
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8


------

That should get you sound.  Even opl3 MIDI works with xplaymidi.

Anyway, hope this helps a few people out.  I started a new thread because there are just so many threads with no solutions regarding this.

---

### Post by Guitar John on 2008-04-06
This worked for me.  Thank you so much.  \\:D/

What I did was:

```
gksudo mousepad /etc/modprobe.d/sound
```  NOTE: this is on a clean install of xubuntu, which uses mousepad for it's test editor.   

Thanks to ugm6hr for [his reply]("http://ubuntuforums.org/showthread.php?t=747336").

Then I used the code provided byPianoman72 along with the edit supplied by walzi to come up with this:

```
blacklist snd-opl3sa2
alias snd-nm256 snd-sb8
alias snd-card-0 snd-sb8
options snd-card-0 index=0
options snd-sb8 irq=5 port=0x220 dma8=1
install snd-sb8 /sbin/modprobe snd_seq; /sbin/modprobe snd_opl3_synth; /sbin/modprobe --ignore-install snd-sb8 && /usr/sbin/alsactl restore >/dev/null 2>&1 || :
remove snd-sb8 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb8
```

Save and close file.

Reboot and VIOLA, I have sound.

Thanks again to all,
John

---

### Post by Tidoo2001 on 2008-06-22
OK...  I know Windows. I know nuttin' 'bout Xubuntu but I'm really beginning to like it!

So how does one get to the BIOS?

How does one create a modprobe.conf file?

How does one even begin to find and install drivers for Xubuntu? 
I am so freaking lost?

Thanx,
Tim D.

---

