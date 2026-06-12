---
title: "&quot;Display Server&quot; Issue"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by trump29 on 2009-02-10
Hi all,

First of all, I'm trying to install Linux Mint and being new to Linux I'm not clear on the relationship between Ubuntu and Mint other than Mint uses Ubuntu stuffs and this same error shows up on Ubuntu... so I thought I'd ask you guys. I have some Ubuntu specific questions too. If asking about Mint is naughty I apologize.

I am able to boot from the Live CD with no problem, Linux runs beautifully off of the live CD. I also have no troubles with the installation steps, I partition my drive just fine and get through each of the seven steps without incident. After I click "Finish" and actually start installing, however, things go wrong. The Installation works for a couple minutes in the GUI before flashing to a black screen with a few text lines, the last of which is "Checking battery state..." It will flash very briefly back to the GUI a few times before bringing this up:

> The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0.

I select OK, and the process repeats, flashing up the GUI for a moment before going back to the "Checking battery state..." screen and ultimately showing me the error again. If I leave it all night it will stay on the "Checking battery state..." screen.

The problem seems fairly common from my Googling, and there are lots of solutions, but none work for me (that I could find). People usually point to the video card drivers, specifically nVidia drivers, but since the OS is not yet installed I can't influence them. The Ubuntu recommendation I've seen on other threads is to run some mysterious "alternative CD" that doesn't have the same GUI (or any GUI). I doubt there is a Mint equivalent so where would I be able to find that if I do go Ubuntu instead of Mint?

Since it seems like my video card is not supported it was recommended on IRC that I disable my video card in BIOS and install, then go back once it's installed and fix problems. I don't seem to have the option in BIOS to disable my video card though. I did however remove my video card entirely and insert an ancient ATI Radeon card. I thought if it was a problem with my card that that would surely let me install. I got the same exact error though.

I was trying with the 64 bit version initially. I was told to try 32 bit and I got the same error that way too.

So a few questions for you Ubuntu guys. 1) Using your wealth of expertise do you have any suggestions that I can try to resolve the issue while sticking with Mint. 2) If I go Ubuntu instead of Mint do you think it's work downloading the standard live CD or is it likely to have the same error as Mint since Ubuntu and Mint are closely related? 3) What is this "alternative CD" I've read about, and where can I find it?

Any help would be greatly appreciated. I still would like to try Mint first, but if Mint isn't going to work for me then I'm hoping Ubuntu will.

Thanks!

My stats:
Video Card: [EVGA GeForce 8600 GTS 256MB](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130084)
Processor: [Intel Core 2 Duo E6600](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115003)
Mother board: [MSI P6N SLI Platinum](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130081)

---

### Post by trump29 on 2009-02-11
I have a happy update on my issue, I was able to install both Ubuntu and Mint last night. Yay.

So addressing my own questions in reverse order:

3) I still don't know what the alternative CD is, but I didn't need it.

2) I was able to install Ubuntu 8.10 64 bit with no problems at all. Whatever causes the problem on the Mint install does not affect the Ubuntu install the same. The only problem I did have was post-installation with Ubuntu, and it was the same error but it came up when I tried to turn on advanced effects. I have yet to look into that, but I know when I was searching I found plenty of post-installation info on that problem, so I think the fix is already out there.

1) I'm still not sure how I got Mint installed ultimately. One thing I tried was updating the motherboard BIOS. That didn't seem to help, I got the same error, but I did notice that the installation got further along and wondered if maybe it was freaking out when a screensaver came up. So I started wiggling my mouse around during install. It got further along the next time I did it, but I still got the same error, so I thought maybe it just doesn't hold out very long and how far it gets depends on how quickly I go through the process. So the next few tries I was bolting through the install process. I clicked any random time zone, put in jjjjjj as username and password rather than taking the time to type a real one, skipped language installs, and generally just rocketed through clicking as quickly as I could. Each time I did it I got a little further until finally I did it fast enough and got it installed before the thing freaked out. I was also constantly moving the mouse, and went back into all the compiz effects and turned absolutely everything off while I was waiting for the next thing I could speed click.

I can't see how any of those things worked. I ran out of good ideas and was using "bang it, that will help" logic. Something worked though. Maybe I just got lucky.

Now I'm going to try and resolve the issue post-installation, which is hopefully much more straight forward. If you have any thoughts on that I will certainly accept your assistance.

Thanks!

---

