---
title: "Support for LG Blu-Ray Disc Burner"
date: 2008-09-10
forum: Hardware
---

### Post by The Foz on 2008-09-10
I just bought an LG BE06LU10 Blu-Ray Disc Burner. It can burn CDs, DVDs, & Blu-Ray discs. Unfortunately, it doesn't work with my Linux server.

I tried it with the old CD/DVD burner software, and with Brasero. It doesn't work. I checked the LG web-site for driver downloads, but there is nothing for Linux. 

I then tried installing the Windows software that LG supplies with the device under Wine. The software installs without problems, but will not run.

I have been reduced to connecting the disc burner to my laptop, which I have to boot with Windows in order to use the burner.  The LG supplied software is good, but this is not an ideal solution.

Does anyone have any better suggestions? 

Does anyone know when such devices are likely to be supported under Ubuntu?

---

### Post by forger on 2008-09-10
Reply with the output of these commands:
```
lspci
lsusb
```

Edit - have you tried this guide:
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

---

### Post by forger on 2008-09-10
Actually.. ignore the above post and read this:
[http://brainstorm.ubuntu.com/idea/935/](http://brainstorm.ubuntu.com/idea/935/)
:)

It's still an idea, and the process of blu-ray/hddvd are patented/copyrighted, so only commercial applications are allowed to use it as far as I know

---

### Post by The Foz on 2009-05-13
I recently installed [Nero Linux 3]("http://www.nero.com/eng/linux3.html"). It works very well the the LG Blu-Ray Burner. I would recommend it for anyone wanting to use a Blu-Ray burner.

The software is freely downloadable with a 30 day trial period.

One limitation that I have discovered in the hardware (the firmware) is that it doesn't seem to be able to burn write-once Blu-Ray discs. Multi-write (RW) discs are fine. This occurs under Windoze as well as linux. For me this is not a problem, but for some of you it might be.

---

### Post by RedRat on 2009-12-09
To me, I want to use it for moving and storing data, being able to watch Blu-ray movies is somewhat down the priority list. I want to be able to send relatives HD video that I shot and Blu-ray has good storage capacity.

As to quality of Blu-ray over standard def movies, frankly even on my 52" LCD, I really don't see that much improvement. Yes it is slightly better but not really worth the premium price you pay right now. The only advantage to commercial Blu-ray titles are all the added features. If I am going to watch a movie, I will watch it on my big screen set, not my computer monitor.

At the end of the day, it appears that Nero Linux is the answer, I will look into it. 

How about Blu-ray burners. LG was mentioned, how about other burners?

---

### Post by agatek on 2010-01-24
> **The Foz said:**
> I recently installed [Nero Linux 3]("http://www.nero.com/eng/linux3.html"). It works very well the the LG Blu-Ray Burner. I would recommend it for anyone wanting to use a Blu-Ray burner.

The software is freely downloadable with a 30 day trial period.

One limitation that I have discovered in the hardware (the firmware) is that it doesn't seem to be able to burn write-once Blu-Ray discs. Multi-write (RW) discs are fine. This occurs under Windoze as well as linux. For me this is not a problem, but for some of you it might be.

To update the thread if somebody looks for related info: right now there is Nero 4 available and I have checked it with a newer LG burner BE08. No problem with both BD-R DL and BD-RE DL. I have not tested with SL but I do not expect here any troubles if it works with DL.

---

### Post by RedRat on 2010-01-24
> **agatek said:**
> To update the thread if somebody looks for related info: right now there is Nero 4 available and I have checked it with a newer LG burner BE08. No problem with both BD-R DL and BD-RE DL. I have not tested with SL but I do not expect here any troubles if it works with DL.
Hey thanks for the info. I might look into that LG burner. Been thinking of Blu-ray burner.

---

### Post by jsmnuk on 2010-02-13
> **RedRat said:**
> To me, I want to use it for moving and storing data, being able to watch Blu-ray movies is somewhat down the priority list. I want to be able to send relatives HD video that I shot and Blu-ray has good storage capacity.

As to quality of Blu-ray over standard def movies, frankly even on my 52" LCD, I really don't see that much improvement. Yes it is slightly better but not really worth the premium price you pay right now. The only advantage to commercial Blu-ray titles are all the added features. If I am going to watch a movie, I will watch it on my big screen set, not my computer monitor.

At the end of the day, it appears that Nero Linux is the answer, I will look into it. 

How about Blu-ray burners. LG was mentioned, how about other burners?

My LG GGW-H20N (non-Lightscribe) has served me well, and I make my own Blu-Ray movies.

One thing to consider with making your own movies is, when you show them on an HDTV, connect an HDMI-to-HDMI cable from the Blu-Ray camcorder to the TV. The image can be stunning in its clarity, and people will see how much better Blu-Ray can be. As for using this cable to feed the image from the camcorder to your computer, it's not an option unless you have an HDMI-in video card. BlackMagic sells them for about $200, but you lose the coaxial connector. You lose some quality through a USB cable from camcorder to computer.

Also, compare Nero Linux 4 to Windows Nero 9 with a Blu-Ray plug-in. In 9, you can load Blu-Ray files, edit them, compile them and burn them to a BD-R or BD-RE disc which will play in another Blu-Ray player. Nero Linux 4 is no more than a compiler and/or a burner. It won't even PLAY Blu-Ray discs.

Does anybody out there want to do anything with Blu-Ray in Linux besides bust Hollywood's encryption? I can't believe that Linux is so far behind the curve in this instance.

---

### Post by RedRat on 2010-02-13
> **jsmnuk said:**
> My LG GGW-H20N (non-Lightscribe) has served me well, and I make my own Blu-Ray movies.

One thing to consider with making your own movies is, when you show them on an HDTV, connect an HDMI-to-HDMI cable from the Blu-Ray camcorder to the TV. The image can be stunning in its clarity, and people will see how much better Blu-Ray can be. As for using this cable to feed the image from the camcorder to your computer, it's not an option unless you have an HDMI-in video card. BlackMagic sells them for about $200, but you lose the coaxial connector. You lose some quality through a USB cable from camcorder to computer.

Also, compare Nero Linux 4 to Windows Nero 9 with a Blu-Ray plug-in. In 9, you can load Blu-Ray files, edit them, compile them and burn them to a BD-R or BD-RE disc which will play in another Blu-Ray player. Nero Linux 4 is no more than a compiler and/or a burner. It won't even PLAY Blu-Ray discs.

Does anybody out there want to do anything with Blu-Ray in Linux besides bust Hollywood's encryption? I can't believe that Linux is so far behind the curve in this instance.

I have a Samsung BluRay player that connects via HDMI cable. My HD video camera connect to the computer via FireWire (1394) connection. When I do connect my camera to the HD TV set, the quality is still stunning.

I too am little interested in busting encryption, as I said most movies I watch once and only very rarely go back and watch it again. Not that many great films, but that is my opinion. 

I agree that it would be nice to be able to edit and burn home made movies to BluRay and play back in the high quality. However, Linux right now is a bit behind the curve on HD editing. Most of the programs out there are not quite there yet and certainly lack polish. However, I expect that to change in the near future. 

To many I would say that comparing BluRay movies to upconverted standard movies from DVDs, again, i don't there is that much improvement in gain for the AVERAGE person. Perhaps if you are in film school or a real afficanado you will see subtely that is just not that apparent to my uncritical eyes. Maybe as I get more experience with doing HD video I will begin to appreciate the differences. I must say that upconversion has come a long, long way in only a few years.

---

### Post by skypuppy on 2011-06-04
I have an LG  blu-ray reader/burner and am severely disappointed in the lack of Linux support.  I, too, wish to put my hd video onto blu-ray discs for the rest of the family (and a couple friends) but can't do so yet.  I bought the BlackMagic card, 6 one-terabyte SATA drives for RAID array, and etc.  (Blu-Ray takes *enormous* resources.  A single SATA drive, even at "3 gb/sec" ((year, right)) didn't even come close to being fast enough for the hd data stream.)
Using Vista for making the discs is just backwards, IMO.

Also, with the price of blu-ray discs, worm or r/w, it is not economical yet to use them to copy commercial movies.  IMO.

signed,
impatiently waiting for hd support.

---

### Post by simonjpo on 2011-06-27
Interesting discussion; puts the cap on my thoughts about buying a 'burner.
Here's a thought - my new TV came with a USB port and has the ability to show original files, including HD, of quite a few formats.
A 16 or 32 G pen drive will enable Linux users to produce and use HD video and show the original rendering on a pen drive plugged into the TV.
No need for a burner, or a player for that matter.
If you really wanted to blow Blu-Ray home movies away, a 500G WD USB-powered drive will set you back about £40($60), and will store a lot of HD Video.
Of course, none of this gives you commercial movies, but I don't particularly want to be locked into proprietary technology standards. As somebody already implied, most of the produce on discs isn't that great, and I do Linux partly to see how little I can spend compared to my relatives.:)

---

### Post by auslander on 2011-11-06
Does anyone know if this drive is supported on eSATA as well as USB?

---

### Post by skypuppy on 2011-11-07
In the US, the Supremes have said it is legal for us to make copies in our own home for our own use -- remember the videotape fiasco with Ho$$ywood taking the ****-end opinion?  If I know how, I would break the hdcp thing so we could make the at home duplicates; not to MENTION putting our (now ubiquitous) hd camcorder stuff onto blu-ray discs.  Hollywood really stuck it to us this time.  I don't know how to vote with my dollars to tell *them* to go stick it.
Grrrr.

---

