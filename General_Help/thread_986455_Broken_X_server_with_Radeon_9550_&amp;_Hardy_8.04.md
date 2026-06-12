---
title: "Broken X server with Radeon 9550 &amp; Hardy 8.04"
date: 2008-11-18
forum: General Help
---

### Post by torbi on 2008-11-18
Hi there!

Everything was going reasonably well with my Ubuntu Hardy 8.04 desktop computer, until yesterday when I opened a Virtual Box session and it crashed my X session. I have a Radeon 9550 card.

When I logged in again, my screen resolution was 800x600, but I had no way of changing it back to 1600x1200. Looking in System > Prefs > Screen resolution, there was not even a drop down selection of different resolutions. 

(Actually, my Radeon 9550 card with Hardy has been causing me trouble since day one - it seemed to freeze my whole computer when I used "Extra" in System > Prefs > Appearance > Visual effects. The second setting "Normal" worked OK and crashless. Same issue with using any 3D game like Open Arena. The freeze would be non-responsive, forcing a reset... but I digress)

I then tried to reinstall my driver. Thus began a cycle that kept me busy for hours last night. I tried to uninstall the fglrx drivers, delete xorg.conf and let Hardy auto discover & use open source drivers but still the same result, same resolution. It even hung after the log in screen (something that mystified me!)

So - my question is - what can I do? How can I somehow restore my machine back to a working state? I have work to do and instead I've been trying to troubleshoot it. I always try to solve my own problems, I have already spent several hours trawling through forums but to no avail.

I think that the best place to start would be somehow resetting my X config back to the state Hardy creates on first install.

The other thing is - could my video card be the issue? Is it possible that the card is somehow damaged?

If you need any logs/other info - please let me know. 

I appreciate your time and thanks for reading,

Torbi

---

### Post by torbi on 2008-11-19
Back with more!

Trying to find a way to reset my xconfig. I have been working on this for a while. I have deleted xorg.conf and rebooted, installed the trident open source drivers, removed the fglrx drivers.. etc and still no joy.

To show you what is shown in System >> Prefs >> Screen Resolution, I grabbed a screen shot of the window. As you can see -there is no way of adjusting the screen resolution,

[IMG]http://i205.photobucket.com/albums/bb46/gemear/Screenshot-MonitorResolutionSetting.png[/IMG]

Any help appreciated! :-)

---

### Post by torbi on 2008-11-19
After some mucking around, I realise that this issue might be a hardware issue.

After Ubuntu giving me a fair amount of grief (very unusual!) I decided to boot up my XP system as my desktop is dual boot. After doing this, the system would hang at around the time I would usually log in.

I then tried swapping DVI from the Radeon card, and instead used VGA.

Voila! Windows booted up fine. 

I rebooted and went back to booting up Ubuntu, which it did, at proper resolution.

So - I am convinced this is the actual card playing up. I guess it's time to "upgrade"! I want to get a well supported Ubuntu card.

Thanks for reading my dilemma. I'm glad it was not Ubuntu's fault!

:guitar:

---

