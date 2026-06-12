---
title: "[SOLVED] Can't Boot WIndows"
date: 2008-09-11
forum: General Help
---

### Post by talking Llama on 2008-09-11
Recently I dual booted Windows XP and Ubuntu but my partition for windows was too small so I booted the Ubuntu Live Diska nd resized the partitions on my hard drive. For some reason Windows XP says it cannot load now and in Ubuntu when I try to click on it it says it cannot be mounted. Though Ubuntu works perfectly, can anyone help me please?

---

### Post by caljohnsmith on 2008-09-11
If you have your Windows Install CD, run a chkdsk and that may be all you need to do to get windows working again:
```
chkdsk /r
```
You have to go into the "recovery console" from the Windows Install CD to get a command prompt.

---

### Post by talking Llama on 2008-09-11
I tried this and it all worked successfully but for some reason I can still only get to the Windows XP login screen. It goes through the Windows XP loading bar section then to the login screen but a login option never comes up... Thanks for your help though.

---

### Post by caljohnsmith on 2008-09-11
> **talking Llama said:**
> I tried this and it all worked successfully but for some reason I can still only get to the Windows XP login screen. It goes through the Windows XP loading bar section then to the login screen but a login option never comes up... Thanks for your help though.
So did chkdsk report any errors? And can you mount your Windows partition in Ubuntu yet? If you can, it would be a good idea to make sure your important files are backed up. It sounds like you may have to do a "Windows repair" from your Windows Install CD at this point if you want to try and recover Windows. Let me know how it goes.

---

### Post by talking Llama on 2008-09-11
It did report errors and it said they were fixed, I'm not entirely sure... How do I go about repairing the Windows installation then? ALso when I tired to mount the Windows partition in Ubuntu I got the message displayed in the picture attachment.

---

### Post by caljohnsmith on 2008-09-11
Just boot your Windows Install CD, and when the main menu comes up and one of the options says "To setup Windows XP now, press ENTER", so press enter. Next select the XP installation you want to repair from the list it gives and press R to start the repair. Be careful to do a repair and not a full reinstall unless you don't mind losing everything that you have in Windows.

---

### Post by talking Llama on 2008-09-11
Ok did a repair, now XP works again, still got everything (wheh!) but for some reason it takes ages to boot now and it refuses to come out of 640x480 resolution and 4 bit colour even once i've installed the correct drivers?

---

### Post by caljohnsmith on 2008-09-11
> **talking Llama said:**
> Ok did a repair, now XP works again, still got everything (wheh!) but for some reason it takes ages to boot now and it refuses to come out of 640x480 resolution and 4 bit colour even once i've installed the correct drivers?
If you do a Windows repair, it knocks you back to Service Pack 1 (SP1) usually; therefore you'll need to update your Windows from the internet so you can get SP2, SP3 and all the other updates since then. Open your Internet Explorer, go to the "tools" menu, and select the "Windows update" option (or whatever it is exactly called). Once you have all the Windows updates downloaded and installed, hopefully that will help your problems. Let me know how it goes.

---

### Post by talking Llama on 2008-09-11
Thank you very much for all your help by the way. I tried this and got through to the windows update website but it says its checking my computer to see if it has the latest software installed and says it'll run an active x piece of software that I should allow to be run but this never appeared and I wanited to check for it for 10 minutes...?

---

### Post by caljohnsmith on 2008-09-12
> **talking Llama said:**
> Thank you very much for all your help by the way. I tried this and got through to the windows update website but it says its checking my computer to see if it has the latest software installed and says it'll run an active x piece of software that I should allow to be run but this never appeared and I wanited to check for it for 10 minutes...?
You're welcome, hope we can get your Windows working again. With Internet Explorer, try going to:

[http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com)

And see if you can get any further this time; if it asks you to install Active X or something, be sure to say yes.

---

### Post by talking Llama on 2008-09-12
I tried going to there but all I get is the message displayed in the attachment but I never get an Active X warning it just stays like that. I left it like that for 15 minutes once to be sure it didn't come up.

---

### Post by caljohnsmith on 2008-09-12
> **talking Llama said:**
> I tried going to there but all I get is the message displayed in the attachment but I never get an Active X warning it just stays like that. I left it like that for 15 minutes once to be sure it didn't come up.
Is your XP a validated version or are you using a pirated copy? That might have something to do with it. Also, it might be enough to go to Start > Settings > Control Panel > Automatic Updates, turn that on, and let the computer sit around a while until Windows figures out it needs to download a bunch of updates. If that doesn't work, you could at least manually download SP2, and that might be enough to get the update feature in IE to work.

---

### Post by talking Llama on 2008-09-13
Nah my copy of Windows is 100% legal and I also tried turning automatic updates on too as Microsoft suggested it but that didn't seem to work. I'll try to download SP2 separately, how would I go about doing that?

---

### Post by caljohnsmith on 2008-09-13
I think you can get [SP2 from this Microsoft web page]("http://www.microsoft.com/downloads/details.aspx?FamilyID=049C9DBE-3B8E-4F30-8245-9E368D3CDB5A&displaylang=en").

---

### Post by kokkus on 2008-09-13
nvm
wrong thread lol

---

### Post by talking Llama on 2008-09-13
Thanks very much. I'll try this and get back to you on how it's going. ^-^

---

### Post by talking Llama on 2008-09-14
Right, I've done this, got SP2 installed but eh updates feature doesn't work, the website updates don't work but at least it displays properly now. Lol. To be honest I wouldn't mind reinstalling too much, I don't have any personal data on their, I just used Windows for gaming, it's just a little bit of a bother reinstalling it but it's not too much hard work. Also randomly the updates window from the control panel takes ages to load and it refuses to load the windows firewall at all. Lol. Thanks for all you're help though. It's been awesome! You've been really helpful to me! ^-^ Unless you have any more suggestions i'll take the coward's way out and reinstall! Lol.

---

### Post by caljohnsmith on 2008-09-14
> **talking Llama said:**
> Right, I've done this, got SP2 installed but eh updates feature doesn't work, the website updates don't work but at least it displays properly now. Lol. To be honest I wouldn't mind reinstalling too much, I don't have any personal data on their, I just used Windows for gaming, it's just a little bit of a bother reinstalling it but it's not too much hard work. Also randomly the updates window from the control panel takes ages to load and it refuses to load the windows firewall at all. Lol. Thanks for all you're help though. It's been awesome! You've been really helpful to me! ^-^ Unless you have any more suggestions i'll take the coward's way out and reinstall! Lol.
Glad when I can help out. :) I suppose you might as well do the full reinstall since it doesn't sound like you have any thing to lose at this point. Before you do that, I would save that "service pack 2.exe" file (or whatever the download is called) to another partition so that you won't have to download it again, because you'll certainly need it after a full reinstall. Let me know how it goes.

---

### Post by talking Llama on 2008-09-17
Cool, I've decided to buy another hard drive and to avoid having to re-size partitions again I'll have one hard drive for each OS. Thanks so much for you're help though, you've been the most helpful person I've found on here yet and everyone on this site is so helpful anyway! Thanks! ^-^

---

