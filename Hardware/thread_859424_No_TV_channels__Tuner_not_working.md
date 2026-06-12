---
title: "No TV channels / Tuner not working"
date: 2008-07-14
forum: Hardware
---

### Post by FirefoxRocks on 2008-07-14
I am running Ubuntu 8.04 and I have a built-in Hauppauge HVR-1250 TV Tuner card that came with my computer when I bought it.

It seems to recognize the card when I did **dmesg** and **lspci**, but I can't get it to work. I have opened up the Add/Remove Programs box under Applications and have tried using every program that says "TV" in it, but none of them did anything.

I also have followed instructions from [http://ubuntuforums.org/showthread.php?t=849528](http://ubuntuforums.org/showthread.php?t=849528), but it didn't help. I have did apt-get on many things (i don't know half the things I'm downloading) but it still doesn't work. I have installed VDR and have enabled it but I still need channels.conf.

Following the advice from Totem's page, I tried using w_scan to generate a listing, but it is unable to open /dev/dvb/adaptor0/frontend0. I think that the only problem is with channels.conf, but I'm not too sure.

Can someone help me here?

(By the way, this works with Windows Media Center on Windows Vista Home Premium perfectly)

---

### Post by FirefoxRocks on 2008-07-17
bump

---

### Post by FirefoxRocks on 2008-07-20
Can anyone please help me with this issue? It would help me use Linux more and not reboot into Windows more often.

---

### Post by FirefoxRocks on 2008-07-27
bump...

---

### Post by theonlyrealperson on 2008-07-28
I have this same card, and it worked out of the box in Debian Lenny. I can tell you for sure two things:

1. It uses the cx23885 kernel modules.
2. The IR receiver (and remote control) are not going to work. 

Since it is supported out-of-the-box with Debian Lenny, it has to be supported in Ubuntu 8.04... Check your kernel version, it worked with mine with kernels 2.6.24 and 2.6.25. 

I also noticed that the DVB cards will only work with certain TV-type programs. The only one I've ever used it in is MythTV, which is really a snap to set up in Ubuntu. 

Make sure those drivers are loaded:

# sudo modprobe cx23885

Then give MythTV a shot, it can't hurt.

---

### Post by steefjeqv on 2008-08-02
> **FirefoxRocks said:**
> I am running Ubuntu 8.04 and I have a built-in Hauppauge HVR-1250 TV Tuner card that came with my computer when I bought it.

It seems to recognize the card when I did **dmesg** and **lspci**, but I can't get it to work. I have opened up the Add/Remove Programs box under Applications and have tried using every program that says "TV" in it, but none of them did anything.

I also have followed instructions from [http://ubuntuforums.org/showthread.php?t=849528](http://ubuntuforums.org/showthread.php?t=849528), but it didn't help. I have did apt-get on many things (i don't know half the things I'm downloading) but it still doesn't work. I have installed VDR and have enabled it but I still need channels.conf.

Following the advice from Totem's page, I tried using w_scan to generate a listing, but it is unable to open /dev/dvb/adaptor0/frontend0. I think that the only problem is with channels.conf, but I'm not too sure.

Can someone help me here?

(By the way, this works with Windows Media Center on Windows Vista Home Premium perfectly)

Hi,

w_scan probably doesn't work because VDR may be running and uses your dvb card.

First stop VDR  (in terminal):

sudo /etc/init.d/vdr stop

Then try w_scan. You may need to use "sudo w_scan".

Greetings,
Steven

---

### Post by FirefoxRocks on 2008-08-22
> **steefjeqv said:**
> Hi,

w_scan probably doesn't work because VDR may be running and uses your dvb card.

First stop VDR  (in terminal):

sudo /etc/init.d/vdr stop

Then try w_scan. You may need to use "sudo w_scan".

Greetings,
Steven
Ok w_scan doesn't report errors now, in fact it doesn't report anything. The channels.conf file is blank. How long does it usually take and how do I know it is doing something?

---

### Post by steefjeqv on 2008-08-22
Hi,

Normally, it scans the frequency range and tells you if there's a signal or not.

You can try the following :

sudo w_scan > /home/yourusername/channels.conf

Then a channels.conf should show up in your home folder.

You can also try out Kaffeine. It's available through synaptic and it works great with digital TV. When your TV card is detected correctly you'll see an icon called "Digital TV".

Always make sure that VDR isn't running when another application needs to use your TV card.

Greetings,
Steven

---

### Post by FirefoxRocks on 2008-08-22
> **steefjeqv said:**
> Hi,

Normally, it scans the frequency range and tells you if there's a signal or not.

You can try the following :

sudo w_scan > /home/yourusername/channels.conf

Then a channels.conf should show up in your home folder.

You can also try out Kaffeine. It's available through synaptic and it works great with digital TV. When your TV card is detected correctly you'll see an icon called "Digital TV".

Always make sure that VDR isn't running when another application needs to use your TV card.

Greetings,
Steven
The channels.conf file is blank. I have installed Kaffeine but it doesn't load.

Here is my terminal output for w_scan:

w_scan version 20080105
Info: using DVB adapter auto detection.

---

### Post by steefjeqv on 2008-08-23
Hi,

I believe Canada uses the ATSC standard.

You'll have to use -fa option for w_scan :

sudo w_scan -fa

This should work.

Greetings,
Steven

---

### Post by steefjeqv on 2008-08-23
Hi,

Give "Me TV" a try, it supports ATSC out of the box. It's available in synaptic.

VDR and Kaffeine are developed for the DVB standard and require patching before they recognize ATSC.

Greetings,
Steven

---

### Post by FirefoxRocks on 2008-08-23
It's been running for about a few hours now in the Terminal window doing nothing, same output as above. The channels.conf file is still blank.

---

### Post by FirefoxRocks on 2009-05-03
By the way, I found out that Canada stil uses the NTSC standard (it will use ATSC in 2011). I have downloaded a whole bunch of TV viewing software (Me-tv, MythTV, tvtime, Kaffeine, Klear, xine) and some other related software I guess (vdr, dvb stuff, etc) but I still have no luck.

And I am using Ubuntu 9.04 now.

---

### Post by maxw on 2009-05-03
I have same problem for a long while with Hauppauge 150MCE. Previously, someone posted this solution which works for me.

In terminal window type:

ivtv-tune -c ##
totem /dev/video0

## is the channel number, of course. I need to use channel 3 for cable.

This isn't a very elegant way to watch tv, but confirms to me that it isn't hardware issue.

IMO, the tvtime and other packages don't seem well supported. 

MaxW

---

### Post by snowman63 on 2009-05-05
I have the same card and after trying everything I could find it still doesn't work. This is a real deal breaker for me. Windows works and not Ubuntu with the HVR-1250. I guess Bill win this battle.

This is why most people say Linux is not ready for the average user.

---

