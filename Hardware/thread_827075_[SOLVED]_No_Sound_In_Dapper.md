---
title: "[SOLVED] No Sound In Dapper"
date: 2008-06-12
forum: Hardware
---

### Post by theravenproject on 2008-06-12
HELP!  I have had no sound now for two weeks since I installed Ubun. Dapper Drake-6.06 LTS on my new Gaming Rig.  Ubuntu never was able to detect the Audio Chipset-it is an onboard chip:

Audio	

   1. Realtek ALC889A codec
   2. High Definition Audio
   3. 2/4/5.1/7.1-channel
   4. Support for DTS (dts NEO:PC)
   5. Support for S/PDIF In/Out
   6. Support for CD In 

Please help me to try and reinstall this Audio-Manually install the Audio Driver(s) I need or do whatever it takes to get sound!

---

### Post by DirtDawg on 2008-06-12
I know this does not address your issue, but you should *really* consider installing Ubuntu's most recent release, Hardy, instead. Dapper is over 2 years old now and chances are you will have much better luck with the sound (among other things) using Hardy.

---

### Post by theravenproject on 2008-06-12
Thank you for the suggestion-You are the 500th person to do so...Really though-My Hardy Live CD that I got Via mail from Canonical failed to work becuase their is no support for my Video card (MSI w/Nvidea 8400 GS) and so I had to use this versin of Dapper that I had from when I first used Linux two years ago-Now I am considering getting a different Distro entirely!  Anyways-I realize I should get Hardy; I really need to keep Dapper at the Moment becuase it is working great except for the sound and I have a $4,000 Gaming cpu w/no OS other than Dapper until I can afford a professional Win XP pro install and Then a Hardy or Latest Distro Install!  **In the mean time-can someone please help me walk through getting this sound to work?  I need someone to walk me through rm'ing the ALSA driver files; manually reinstalling them, and if that doesn't work-doing whatever it takes to get this sound to work**  :frown::frown::frown::shock::shock::shock::confused::-(

---

### Post by markharding557 on 2008-06-12
you could try installing nvidia drivers with their installer from their web site when you try hardy again

---

### Post by DirtDawg on 2008-06-12
> **theravenproject said:**
> Thank you for the suggestion-You are the 500th person to do so...

I found [your post concerning the video problems]("http://ubuntuforums.org/showthread.php?t=808705") you had with Hardy. Maybe the biggest problem you had (sans poor post fomatting) was marking the thread as Solved when it clearly is not.

You can continue to use Dapper since you did manage to at least get it running, but you may find (have found?) that support is going to be hard to come by because Dapper is obsolete and most of us have moved on. You will also likely continue to hear that you should upgrade to Hardy. 

The problem you outline in your older post sounds very much like a faulty CD image. I know it's frustrating since you got the cd from Canonical, but maybe you could try [burning your own copy]("https://help.ubuntu.com/community/BurningIsoHowto"). It makes little sense that Dapper would support your card, but the support would be dropped on later Ubuntu releases.

Also, there is a live CD option to check the CD for defects. You may want to try that because even one corrupt file means a no go. You could also try using the alternate-install cd. Or, I would even suggest installing Gutsy and attempting to upgrade to Hardy before regressing to Dapper. And since you know Dapper works, there's no harm in at least *trying* the Hardy live CD again.

Of course you're free to do as you choose, but bear in mind that you are likely to continue having problems with Dapper because it's old old old.

---

### Post by lswb on 2008-06-12
It may be old old old, (2 years) but at least it doesn't crash crash crash!

---

### Post by markharding557 on 2008-06-13
> **DirtDawg said:**
> I found [your post concerning the video problems]("http://ubuntuforums.org/showthread.php?t=808705") you had with Hardy. Maybe the biggest problem you had (sans poor post fomatting) was marking the thread as Solved when it clearly is not.

You can continue to use Dapper since you did manage to at least get it running, but you may find (have found?) that support is going to be hard to come by because Dapper is obsolete and most of us have moved on. You will also likely continue to hear that you should upgrade to Hardy. 

The problem you outline in your older post sounds very much like a faulty CD image. I know it's frustrating since you got the cd from Canonical, but maybe you could try [burning your own copy]("https://help.ubuntu.com/community/BurningIsoHowto"). It makes little sense that Dapper would support your card, but the support would be dropped on later Ubuntu releases.

Also, there is a live CD option to check the CD for defects. You may want to try that because even one corrupt file means a no go. You could also try using the alternate-install cd. Or, I would even suggest installing Gutsy and attempting to upgrade to Hardy before regressing to Dapper. And since you know Dapper works, there's no harm in at least *trying* the Hardy live CD again.

Of course you're free to do as you choose, but bear in mind that you are likely to continue having problems with Dapper because it's old old old.

dapper drake is not obsolete it is suppoted untill 06/09 because it is an lts release

---

### Post by theravenproject on 2008-06-18
Thanks all of you and I was under the same impression as markharding557 in that Dapper was an LTS release and should be supported for three years from it's release date so I ought to have about a year yet before it is considered "Outdated" shouldn't I? Anyways-please, somebody, rather than post the benefits of getting Hardy(Believe me, I want to try a newer Distro and Probably will soon-but Dapper is working on this Tempermental thing right now) or taking a jab at my the "Ill Formatting" of my previous posts; can I just get some help with sound?  Now, I am inclined to try uninstalling the Whole ALSA files and then reinstalling them and configuring them to see if that perhaps helps-if perhaps their was some kind of mistake with them during install?  I don't know but I have to try something and I would greatly appreciate the guidance of some of you "More Seasoned" Ubuntu'ers rather than repeated admonishments to migrate to Hardy Heron mixed with chastisements for poorly written or prematurely aborted former posts of mine...Thank anyone for their sincere and earnest help on these matters!

---

### Post by DirtDawg on 2008-06-18
> **theravenproject said:**
> Thanks all of you and I was under the same impression as markharding557 in that Dapper was an LTS release and should be supported for three years from it's release date so I ought to have about a year yet before it is considered "Outdated" shouldn't I? Anyways-please, somebody, rather than post the benefits of getting Hardy(Believe me, I want to try a newer Distro and Probably will soon-but Dapper is working on this Tempermental thing right now) or taking a jab at my the "Ill Formatting" of my previous posts; can I just get some help with sound?  Now, I am inclined to try uninstalling the Whole ALSA files and then reinstalling them and configuring them to see if that perhaps helps-if perhaps their was some kind of mistake with them during install?  I don't know but I have to try something and I would greatly appreciate the guidance of some of you "More Seasoned" Ubuntu'ers rather than repeated admonishments to migrate to Hardy Heron mixed with chastisements for poorly written or prematurely aborted former posts of mine...Thank anyone for their sincere and earnest help on these matters!

Geez. Sorry you took it so hard. Try not to shoot the messenger, I was trying to save you the frustration of getting no answer (which, as you see, is exactly what's happening). I (sincerely) wish you luck with that.

---

### Post by theravenproject on 2008-06-18
I am sorry too DirtDawg..I think we just got off to the wrong foot...Apology accepted and I hope you'll accept mine-I do see the wisdom in what you were trying to convey to me.  What I was trying to communicate (Admittedly somewhat angrily in my last post) was that I am stuck with Dapper at the moment and am grasping for any straws so anyone who reads this who as any Ideas at all as far as Reinstalling the ALSA driver files/OSS driver files etc...I welcome it and will try anything at this point...I do plan on moving to Hardy and am hoping it was just a jacked up Install CD...Again-sorry I got offended and I recant everything I said...thank you for your help DirtDawg...:)

---

