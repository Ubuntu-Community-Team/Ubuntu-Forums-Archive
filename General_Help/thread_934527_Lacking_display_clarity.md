---
title: "Lacking display clarity"
date: 2008-09-30
forum: General Help
---

### Post by ineuw on 2008-09-30
I have a dual boot MS Windows XP/Ubuntu Hardy Heron 8.0.4, with an ASUSTek ATI X1300/X1500 video card.  The monitor is SyncMaster 793DF CRT with .020 pitch, which is quite fine (and is the reason why I bought it). There is 2GB of RAM on the mother board and the video card comes with 256 MB on board and another 256 MB taken from the 2GB memory pool.  My problem is that the display in Ubuntu is fuzzy, regardless of the font I select.

I fiddled with all the possible combinations of the Desktop settings, font display clarity settings, etc.  I tried both the native and the ATI driver available for Ubuntu, but the display results are the same.  The white is not clear white and the contrast and clarity of the character outlines are very poor.  Is there a way to fix this?

Any comment is appreciated, as I really want to get out of Windows, which I must use because of this issue.

---

### Post by dcstar on 2008-09-30
> **ineuw said:**
> I have a dual boot MS Windows XP/Ubuntu Hardy Heron 8.0.4, with an ASUSTek ATI X1300/X1500 video card.  The monitor is SyncMaster 793DF CRT with .020 pitch, which is quite fine (and is the reason why I bought it). There is 2GB of RAM on the mother board and the video card comes with 256 MB on board and another 256 MB taken from the 2GB memory pool.  My problem is that the display in Ubuntu is fuzzy, regardless of the font I select.

I fiddled with all the possible combinations of the Desktop settings, font display clarity settings, etc.  I tried both the native and the ATI driver available for Ubuntu, but the display results are the same.  The white is not clear white and the contrast and clarity of the character outlines are very poor.  Is there a way to fix this?

Any comment is appreciated, as I really want to get out of Windows, which I must use because of this issue.

What happens when you use the "Auto adjust" function on your monitor?

---

### Post by ineuw on 2008-10-01
> **dcstar said:**
> What happens when you use the "Auto adjust" function on your monitor?

Hi David,

Thanks for your reply.  The "auto reset" seemed to have improved it a little bit.  It seems that I stretched the image past the default frame.  Nevertheless, it is still not clear.

---

### Post by tgalati4 on 2008-10-01
What is the resolution and refresh rate between Windows and Ubuntu?  Perhaps your refresh rate is different between the two.  That will affect contrast and sharpness.

Also, is "Anti-alias" turned on or off?

---

### Post by ineuw on 2008-10-01
> **tgalati4 said:**
> What is the resolution and refresh rate between Windows and Ubuntu?  Perhaps your refresh rate is different between the two.  That will affect contrast and sharpness.

Both Windows and Ubuntu are set to 1024 x 768 resolution. After resetting the monitor to its default, the clarity improved a little. 

I re-installed the ATI fglrx driver and this allowed to set the refresh rate to 72 on both systems, so now they are identical.

I also tried different refresh rates in Ubuntu, but there is no difference between 70, 72 and 75.

---

### Post by tgalati4 on 2008-10-01
I remember seeing some display fine-tuning in Gnome, but I don't remember where they are located.  The ATI driver may have some options that can be set.  You would have to do some research to discover these options.

---

### Post by inearlygaveup on 2008-10-17
> **ineuw said:**
> I have a dual boot MS Windows XP/Ubuntu Hardy Heron 8.0.4, with an ASUSTek ATI X1300/X1500 video card.  The monitor is SyncMaster 793DF CRT with .020 pitch, which is quite fine (and is the reason why I bought it). There is 2GB of RAM on the mother board and the video card comes with 256 MB on board and another 256 MB taken from the 2GB memory pool.  My problem is that the display in Ubuntu is fuzzy, regardless of the font I select.

I fiddled with all the possible combinations of the Desktop settings, font display clarity settings, etc.  I tried both the native and the ATI driver available for Ubuntu, but the display results are the same.  The white is not clear white and the contrast and clarity of the character outlines are very poor.  Is there a way to fix this?

Any comment is appreciated, as I really want to get out of Windows, which I must use because of this issue.
Hi ineuw  

I have also updated my Dual OS system from Xandros to Ubuntu  after trying the live DVD. The display while using this DVD was far better than the Xandros (This was also not very good)so I took the plunge and installed it.

Unfortunately, just like you I also find the display very wishy washy, out of focus, to much contrast or something, not really sure what it is but it certainly isn't something I want to stare at for any length of time.

Have you had any other help on this subject, if so could you pass me the link.

I don't want to drop Linux because I really like it,  BUT the display certainly in Google mail hurts my eyes.

Martin

---

### Post by ineuw on 2008-10-17
> **inearlygaveup said:**
> Hi ineuw  

I have also updated my Dual OS system from Xandros to Ubuntu  after trying the live DVD. The display while using this DVD was far better than the Xandros (This was also not very good)so I took the plunge and installed it.

Unfortunately, just like you I also find the display very wishy washy, out of focus, to much contrast or something, not really sure what it is but it certainly isn't something I want to stare at for any length of time.

Have you had any other help on this subject, if so could you pass me the link.

I don't want to drop Linux because I really like it,  BUT the display certainly in Google mail hurts my eyes.

Martin

Sadly, I have nothing new and better to report.  I removed my Linux ATI driver and then I reset the monitor which marginally helped, then I increased the refresh rate and this also seemed to help, but not much, and finally re-installed the ATI driver, but there is no improvement.

I can live with the video quality of Ubuntu, but it is the fuzziness of text that disturbs my eyes, as it has yours.

What make of video card do you have?  Although, I don't believe it matters.  The fact is that Microsoft has a long and close relationship in driver development with all graphics card manufacturers.  Also, Microsoft has been working for years on their text display improvement and this proprietary software is not available in Ubuntu or in the Linux ATI driver.

So now, I use Ubuntu for an hour, or two at most, and the reboot into XP and continue my work.

---

### Post by inearlygaveup on 2008-10-17
Thanks for your reply, I agree with you I can usually only stand it for and hour, to me it feels like working under a spotlight compared to windows. I like the OS programme because I like tinkering!
I am not very technical but I think my Laptop has a ATI Radeon Xpress 1100. The Screen is an Acer CrystaBrite and as it says on the box, it has a Brilliant LCD performance (except on OS Systems) .
I did Google the problem and found a not very good report at 
[http://www.askdavetaylor.com/why_do_the_fonts_in_firefox_linux_look_so_terrible.html](http://www.askdavetaylor.com/why_do_the_fonts_in_firefox_linux_look_so_terrible.html)

I hope they eventually get it right because I would like to change.

Martin

---

### Post by ineuw on 2008-10-17
> **inearlygaveup said:**
> I did Google the problem and found a not very good report at [http://www.askdavetaylor.com/why_do_the_fonts_in_firefox_linux_look_so_terrible.html](http://www.askdavetaylor.com/why_do_the_fonts_in_firefox_linux_look_so_terrible.html)
I hope they eventually get it right because I would like to change.
Martin

Hi inearlygaveup,

The article in your link is related, but does not address our problem.  This is a software clarity display issue with any font, any size, TrueType or else.  I tried TrueType long ago and without any improvement.  So, I changed back to Linux fonts because there was no difference, and because of the questionable nature of TrueType font ownership (Mac or Windows).

That this might be an ATI Radeon problem, (either software or hardware or both), is indicated by the fact that we both have ATI Radeon video cards but, you have LCD and I have CRT, with the identical problems.

There is very little posted on related problems on the web, and perhaps this is because most other users have NVidia or other video cards?  Perhaps others' vision is not so sensitive? I really don't know the answer.

As for a Linux solution, this may not be forthcoming if the problem is related to proprietary driver issues.

---

### Post by jhernandez1270 on 2008-10-17
I'm assuming you are using amdccle?  If not give it a shot

edit: sorry it's amdcccle

---

### Post by ineuw on 2008-10-18
[QUOTE=use amdcccle[/QUOTE]

Thanks for this piece of info.  I never knew about it.  So, I logged into Ubuntu and searched the topic with the result that something is wrong with my Ubuntu installation and I must run an update of everything.  So, this will keep me offline for the next couple of hours and I will get back to you.  I will have to go through all the steps again for the amdcccle and in either case of success of failure, I will post the results.

---

### Post by ineuw on 2008-10-18
> **jhernandez1270 said:**
> I'm assuming you are using amdccle?  If not give it a shot. edit: sorry it's amdcccle

> **ineuw said:**
> Thanks for this piece of info.  I never knew about it.  So, I logged into Ubuntu and searched the topic with the result that something is wrong with my Ubuntu installation and I must run an update of everything.  So, this will keep me offline for the next couple of hours and I will get back to you.  I will have to go through all the steps again for the amdcccle and in either case of success of failure, I will post the results.

It seems that I was missing all updates due to this not being selected in the Administration>>Software sources.  This prevented me from installing amdcccle.  After the updates and reboot, I had no problem to install amdcccle.  Unfortunately, the settings in this panel deal with 3D rendition.  Nevertheless, I moved all settings to midrange and rebooted again.  There seemes to be a marginal improvement in the text displays.

---

