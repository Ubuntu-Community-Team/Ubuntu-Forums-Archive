---
title: "No audio volume control from panel"
date: 2012-10-17
forum: Hardware
---

### Post by BillFann on 2012-10-17
THIS PROBLEM HAS BEEN SOLVED. RE-NISTALLED THE OS.


Greetings one and all.
 

 I'm having an issue with my laptop.
 I'm using an ***HP Pavilion dv7-6135dx Entertainment PC***. 
 The volume control on the top panel won't adjust the volume of my sound. I can hear the sound. I can adjust the sound in a video, but I can't adjust it from the top panel.
 
***OS:***
I'm running UBUNTU 11.04 
(I tried to paste a screen shot of the full data but the shot won't show up in this post.)

***lshw:***
 This is what I get from ***lshw***
 
 Audio device 
 /0/100/1b 
  
  
 product: 6 Series Chipset Family High Definition Audio Controller [8086:1C20] 
 vendor: Intel Corporation [8086] 
 bus info: pci@0000:00:1b.0 
 version: 05 
 width: 64 bits 
 clock: 33MHz 
 capabilities: 
     Power Management, 
     Message Signalled Interrupts, 
     PCI Express, 
     bus mastering, 
     PCI capabilities listing 
 configuration: 
     driver: HDA Intel 
     latency: 0 
 resources: 
     irq: 50 
     memory: c7500000-c7503fff
 
***Device Manager***{
I looked a the ***Device Manager*** (again, the screen shot won't show in this post).

I see an HDA Intel PCH Sound Card with a blue circle containing a "?".

  I believe that this is telling me that the driver is bad. But, if so, why can I still hear sound when I run a movie or play a video from YouTube?
  

  What must I do to re-install the sound card driver (where do I find it and how do I install it?)?
  

  Any other thoughts?
  

  Thanks for your help.
  

  Bill

---

### Post by PowerBarry43 on 2012-10-17
Hi 

open up a terminal and try running
```

alsamixer
```

and see if you can control the volume from there

hope this helps

Barry

---

### Post by BillFann on 2012-10-17
> **PowerBarry43 said:**
> Hi 

open up a terminal and try running
```

alsamixer
```and see if you can control the volume from there

hope this helps

Barry

Barry,
Thank you for the reply.
I tried the alsamixer. The "MM" is grayed out. I did get the "MM" volume to increase (The bar graph went from 0% to 100%), but the volume control on the main screen panel still won't control the volume. 
I wish I could include screen shots. It would make it so much easier to communicate what I see. But, they won't show up in my postings.
Thank you though.
Any further thoughts?
Bill

---

### Post by BillFann on 2012-10-18
It'll be much easier to communicate my situation if I can include screen shots in my posts. I can't seem to find a way to do so. My screen shots are .png files and are below the max size of 947 Mb, but they don't show up in my postings.
Can any of you tell me how to do this?
Thanks,
Bill

---

### Post by valroadie on 2012-10-18
Let me see if this test works...
[ATTACH]225709[/ATTACH]
If so, use the little paper clip above your text reply, upload the image, then you must click the arrow next to the paper clip and select the image to post it.

Yup worked. :) Don't mind my desktop! :P

---

### Post by BillFann on 2012-10-18
> **valroadie said:**
> Let me see if this test works...
[ATTACH]225709[/ATTACH]
If so, use the little paper clip above your text reply, upload the image, then you must click the arrow next to the paper clip and select the image to post it.

Yup worked. :) Don't mind my desktop! :P


valroadie, 

OK, Let me try...

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225711&stc=1&thumb=1&d=1350578958[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=225711&d=1350578958")

It worked.
Thank you!

---

### Post by valroadie on 2012-10-18
You're welcome. :D 

Also I have found this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
Not sure if it is EXACTLY what you're looking for but it mentions your type of laptop and sound drivers so I thought I would throw it on here and see if you could use it. 
Cheers.

---

### Post by BillFann on 2012-10-18
> **valroadie said:**
> You're welcome. :D 

Also I have found this:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
Not sure if it is EXACTLY what you're looking for but it mentions your type of laptop and sound drivers so I thought I would throw it on here and see if you could use it. 
Cheers.


valroadie,
Thank you for the information.
I dried the steps mentioned in your lead. All passed.
I do get sound. I can hear the sound on playback of videos.
What I can't do is control the volume from here:

<I can't get the .odg file to load here, but it shows the main screen with the speaker in the top panel>
   
[Corner of screen .odg]("http://ubuntuforums.org/attachment.php?attachmentid=225713&d=1350583563")


When I click on the speaker, and select Sound Preferences, I get this:

[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225714&stc=1&thumb=1&d=1350583730[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=225714&d=1350583730")

This leads me to suspect the audio card driver. I look at the Device Manager and I see this:


[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=225715&stc=1&thumb=1&d=1350583827[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=225715&d=1350583827")
I re-loaded the device driver, but I still get the same blue circle w questoinmark on the sound driver.

I am at a loss....
Any other thoughts?

Thanks,
Bill

---

### Post by valroadie on 2012-10-18
Well the only thing I can think of doing, is right clicking on the task bar and adding the sound controls icon right onto the task bar = Right click -> Panel -> Mixer. It opens the sound controls window and not the main volume bar which is most likely what you want :(

---

### Post by BillFann on 2012-10-19
> **valroadie said:**
> Well the only thing I can think of doing, is right clicking on the task bar and adding the sound controls icon right onto the task bar = Right click -> Panel -> Mixer. It opens the sound controls window and not the main volume bar which is most likely what you want :(

valroadie,

Thank you for your thoughts.

I tried to add the sound controls as you mentioned. The Mixer option doesn't even appear in the list of things to be added. This gets stranger and stranger.

I have also noticed that there are quite a few missing things under "Places" .  Documents, Videos, and Downloads are missing from the "Places" list. 

I begin to wonder if this is a hardware issue (remember the Device Manager) or a software (OS?) issue.

Thoughts?

Thanks again.

Bill

---

### Post by valroadie on 2012-10-19
Hmm I am not sure it is a hardware issue though it COULD be as far as the sound goes...but things missing from your documents and such is def. a problem. 
I hate to say it but, I would backup all of your documents, music, pictures things like that and try reinstalling the operating system. I know it tkes some time but if the problems turn up again it could be anything from #1: The installation disk itself is corrupt. or #2: A hardware issue. Though the menus not listing in places doesn't sound anything of the hardware type. 
Keep us updated!

---

### Post by Yellow Pasque on 2012-10-20
"Waiting for sound system to respond" means pulseaudio is screwed up. You can still get sound if the program sends the sound directly to the ALSA device (though only one device can use that at a time). Try backing up the pulseaudio config files so it generates fresh ones:
```
cd ~/; mkdir pulsebackup; mv .pulse* pulsebackup/
```
Then, log out and back in. If it's still not working, post pulse verbose log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

Also, note that Ubuntu Natty/11.04 is now EOL. If you don't like to upgrade, you should probably do a fresh install of Ubuntu 12.04

---

### Post by BillFann on 2012-10-21
> **Temüjin said:**
> "Waiting for sound system to respond" means pulseaudio is screwed up. You can still get sound if the program sends the sound directly to the ALSA device (though only one device can use that at a time). Try backing up the pulseaudio config files so it generates fresh ones:
```
cd ~/; mkdir pulsebackup; mv .pulse* pulsebackup/
```Then, log out and back in. If it's still not working, post pulse verbose log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

Also, note that Ubuntu Natty/11.04 is now EOL. If you don't like to upgrade, you should probably do a fresh install of Ubuntu 12.04


Temujin,
Thank you for the response. I really wish I had seen this before I did a complete OS re-install. Oh well. The fates are working here.
In any event, the problem is now solved. 
Thanks again.
Bill

---

### Post by BillFann on 2012-10-21
> **BillFann said:**
> valroadie,

Thank you for your thoughts.

I tried to add the sound controls as you mentioned. The Mixer option doesn't even appear in the list of things to be added. This gets stranger and stranger.

I have also noticed that there are quite a few missing things under "Places" .  Documents, Videos, and Downloads are missing from the "Places" list. 

I begin to wonder if this is a hardware issue (remember the Device Manager) or a software (OS?) issue.

Thoughts?

Thanks again.

Bill


valroadi,

Thanks again for your thoughts.
I re-installed the OS. Problem solved.
Again, thank you for your assitance,
Bill

---

