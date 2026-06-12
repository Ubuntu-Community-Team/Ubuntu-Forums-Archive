---
title: "DMA - How do I turn it on &amp; keep it on?"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by ixus_123 on 2006-10-20
My DVD drive worked fine on breezy but for some reason I can't seem to enable DMA on it in under dapper.  Can anyone help me?

This is what I've done so far
```
kieren@wonderful:~$    sudo hdparm /dev/hdc Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
kieren@wonderful:~$


```
DMA is off so I do this to turn it on. . .
```
kieren@wonderful:~$ sudo hdparm -d1 /dev/hdc 
/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

```
so I want to check it
```
kieren@wonderful:~$    sudo hdparm /dev/hdc

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

Am I missing something?  What's going on?

---

### Post by RichJacot on 2006-10-20
I have the same issue.  I have been unable to find a fix, so I've had to live with checking DMA prior burning EVERY DVD.  I hope you have more luck in getting an answer than I did!

---

### Post by RankHypocrisy on 2006-10-20
This looks like it could be related to the problem I'm running into here -- [http://ubuntuforums.org/showthread.php?t=280518](http://ubuntuforums.org/showthread.php?t=280518)

Except that my problem has to do with my hard drive.

---

### Post by ixus_123 on 2006-11-01
Just finished a clean install of Efty & I still get the same thing.

Is it an Ubuntu bug or a problem with my hardware?

---

### Post by dannyboy79 on 2006-11-04
the command you guyys are using only enables dma for the current session, if you want it permanent, you need to edit /etc/hdparm.conf, just remove the # from your cd or dvd drive label (hda or hdb etc etc) and put the settings you want, that's what this blog says nayway: [http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/](http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/)

 if you have problems, this has been reported to work for red ha_ 9, It has been brought to my attention that Red Hat 8.0 users have reported difficulties enabling DMA on their DVD drives. If you're running that distribution, add the following line to your /etc/modules.conf to fix the problem: options ide-cd dma=1

---

### Post by RichJacot on 2006-11-06
This is what I have had in my /etc/hdparm.conf for some time now.

# I uncommented the following 4 lines to see if it helped with
# the DMA problem on my dvd drive.  RJ
/dev/hda {
        io32_support = 1
        dma = on
}

DMA is on after a reboot for at least a few burns then it turns off.  It's not always the same number of burns.  Sometimes I can burn 15 or 20 DVD's and other times it turns off after only 5 or 6 burns.

---

### Post by dannyboy79 on 2006-11-07
well i think you need to set it so that it's "1" not "on", just like your io32_support setting. Here is what my hdparm.conf has in it:

command_line {
       hdparm -q -m16 -q -W0 -q -d1 -q -A1 -q -u1 -q -c1 -q -X69 -q -S12 /dev/hd                            a
}

i decided to use the command line option way, i read thru man hdparm.conf really well and I think my dma settings stay put when I restart. i'll let you know if they don't the next time I shut down, since it a server, I don't shut it down very often.

---

### Post by RichJacot on 2006-11-07
Thank you, I will give your suggestion a try and see how it goes.

Since you mention that this is a server, how much burning do you do with it?

Again, Thank you!

---

### Post by dannyboy79 on 2006-11-07
just because I say it's a server doesn't mean it can't also be a desktop, i have it serving an ftp site, as well as serving media to me xbox, as well as being a backup server, soon I want to play around with making my own web server just to learn about it. possibly a mail server but not sure about that. so to answer your question, i burn about 5 discs a week, and I really hate having to ftp files or folders over to my winbloz box just so that I can burn them onto a dvd!

---

### Post by RichJacot on 2006-11-23
My settings are now the same as yours, except my is /dev/hdc.  After a reboot I have:
```
/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```


I'll be burning a bunch over the holiday, so it will be a good test.

Rich

---

### Post by RichJacot on 2006-11-28
Hello,

Well DMA still turns itself off after a number of burns.

```
sudo hdparm /dev/hdc
Password:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off) 
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


sudo hdparm -d1 -k1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 setting keep_settings to 1 (on)
 using_dma    =  1 (on) 
 keepsettings =  1 (on)
$
```

Does anyone have any further ideas?

Thanks!

---

### Post by dannyboy79 on 2006-11-28
i found out that within my syslog or some other log file, my dvd burner didn't support the dma setting that I chose. So your's might be the same thing? it's within dmesg:

hda: Speed warnings UDMA 3/4/5 is not functional.
[17179590.760000] hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
[17179590.760000] hda: set_drive_speed_status: error=0x04 { AbortedCommand }
[17179590.760000] ide: failed opcode was: 0xef
[17179590.760000] hda: Speed warnings UDMA 3/4/5 is not functional.

i guess it's time to buy a brand name burner and not this i/o magic crap! good luck

---

### Post by RichJacot on 2006-11-30
My DMA being disabled appears not be related to "burning". It appears to just be accesses (or something ](*,) ).  I have been ripping and encoding my CD collection, with no dvd burning, and I'm still having the problem.  Needless to say the ripping takes MUCH longer once DMA disables itself.

My messages file has:

```
Nov 29 22:12:45 defiant kernel: [17194737.428000] hdc: irq timeout: status=0xd0 { Busy }
Nov 29 22:12:45 defiant kernel: [17194737.428000] ide: failed opcode was: unknown
Nov 29 22:12:45 defiant kernel: [17194737.428000] hdc: DMA disabled
Nov 29 22:12:48 defiant kernel: [17194741.316000] hdc: ATAPI reset complete

```

My /etc/hdparm.conf has:

```
command_line {
       hdparm -q -m16 -q -W0 -q -d1 -q -A1 -q -u1 -q -c1 -q -X69 -q -S12 /dev/hdc
}

```

Are there any other files anyone would like to see to help me troubleshoot this problem further?  
Does anyone have any suggestions?  

I am at a loss. ](*,)

---

### Post by dannyboy79 on 2006-11-30
looks to me like something may be wrong with your kernel. it states "defiant kernel". i would just look at all your logs. anything that has a recent date that's inside /var/log/ or just /var/. good luck, let me know what you find

---

### Post by ixus_123 on 2007-01-12
My case turned out (I think) to be hardware failure.

DMA wont stay on in Windows either. I was worried it might be the mainboard but I've just spent £20 on a new sony DVD rw drive & that works fine.  

Words can't describe how happy I am to have DMA back & be able to burn DVDs & watch DVDs with out them jittering :D

Thanks to everyone that offered help

---

### Post by b00gie on 2007-03-27
Hello!

I had the same issue as you guys but it's solved now.


My suggestion is to forget any changes in /etc/hdparm.conf. Then use UDMA66 cable instead of UDMA33 (i mean 80 lines instead of 40) to connect your CD/DVD drive to motherboard. Next thing is to enable proper module that support your mobo's chipset. Mine is alim15x3 (my motherboard is Asrock 939DUAL-SATA2). To do it i had to put ```
alim15x3
```as a 1st line to /etc/modules. Next reboot and now DMA on DVD drive is permanent :)

Cheers!

---

### Post by dannyboy79 on 2007-03-28
could you explian this a little more? I didn't know they made modules for specific motherboards? or are you talking about the ide chipset? can you please specify what you mean? thank you.

---

