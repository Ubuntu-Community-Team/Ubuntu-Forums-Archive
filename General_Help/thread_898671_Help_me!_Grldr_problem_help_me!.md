---
title: "Help me! Grldr problem help me!"
date: 2008-08-23
forum: General Help
---

### Post by Mr newb on 2008-08-23
Ok today I downloaded the latest version of ubuntu extracted it with winrar and ran wubi which installed linux. Then at the end of the installation I restarted my computer when I select ubuntu in the boot manager here is what comes up:
[COLOR="Red"]
Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart.[/COLOR]


Ok so my computer is an hp with windows vista premium 512mb of ram 160gb hardrive. I am not a super genius with computer I know that basic, I just need to know how to fix it because I have tried ubuntu before and it was FANTASTIC very great.
If it helps here are some screen pictures.

Here is what my computer looks like:

[IMG]http://i89.photobucket.com/albums/k228/ilovemonkey4life/comp.jpg[/IMG]

Here is my ubuntu folder located at C:\ubuntu

[IMG]http://i89.photobucket.com/albums/k228/ilovemonkey4life/ubuntu.jpg[/IMG]






Thank you for reading PLEASE HELP ME I REALLY WANT TO UBUNTU
BTW I AM NOT THAT SMART SO PLEASE MAKE IT SIMPLE.:confused:

---

### Post by overdrank on 2008-08-23
Hi and welcome, I do not use Wubi but one issue maybe that I do not think you need to extract the iso if you are using wubi. Just put the iso in the wubi folder. If you burn the iso to disc then you can install from with in windows. But as I said I am no expert with Wubi. :)

---

### Post by Mr newb on 2008-08-23
there is no wubi folder do i just take the iso that i downloaded and burn it to a cd?

---

### Post by overdrank on 2008-08-23
> **Mr newb said:**
> there is no wubi folder do i just take the iso that i downloaded and burn it to a cd?

Yes that is one option, you may also look at the Wubi FAQ's
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Mr newb on 2008-08-23
so i just use your link to install it?

---

### Post by Mr newb on 2008-08-23
same exact installer i use the first time

---

### Post by Mr newb on 2008-08-23
it didnt work

---

### Post by overdrank on 2008-08-23
Moved to Wubi. :)

---

### Post by Mr newb on 2008-08-23
Ok today I downloaded the latest version of ubuntu extracted it with winrar and ran wubi which installed linux. Then at the end of the installation I restarted my computer when I select ubuntu in the boot manager here is what comes up:
[COLOR="Red"]
Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart.[/COLOR]


Ok so my computer is an hp with windows vista premium 512mb of ram 160gb hardrive. I am not a super genius with computer I know that basic, I just need to know how to fix it because I have tried ubuntu before and it was FANTASTIC very great.
If it helps here are some screen pictures.

Here is what my computer looks like:

[IMG]http://i89.photobucket.com/albums/k228/ilovemonkey4life/comp.jpg[/IMG]

Here is my ubuntu folder located at C:\ubuntu

[IMG]http://i89.photobucket.com/albums/k228/ilovemonkey4life/ubuntu.jpg[/IMG]






Thank you for reading PLEASE HELP ME I REALLY WANT TO UBUNTU
BTW I AM NOT THAT SMART SO PLEASE MAKE IT SIMPLE.:confused:

An admin moved this to the wubi section but that didnt help, will someone help me

---

### Post by Sycron on 2008-08-23
> Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (0,2): invalid or null
Try (hd0,3): invalid or null

AFAIK it should be **Try (hd0,2)** not **Try (0,2)**.

---

### Post by Mr newb on 2008-08-23
ok i still need help

---

### Post by unca.paka on 2008-08-23
It looks like the boot loader wubi installed got brutalized. never used wubi to install personally, but it seems its using something like ntldr.

Try reinstalling, goto Control Panel/Add-Remove Programs(or however Vista handles it) Remove Wubi, then try to install again.

Also take a look at 
[http://ubuntuforums.org/showthread.php?t=396526]("http://ubuntuforums.org/showthread.php?t=396526") 
might be something useful in there.

---

### Post by Mr newb on 2008-08-23
it still says the same thing
:confused:

---

### Post by Ryadt on 2008-08-23
Is there any particular reason as to why you extracted the iso?

---

### Post by Mr newb on 2008-08-23
so i can install it because the iso was like a winrar archive i still have the iso though

---

### Post by unca.paka on 2008-08-23
Should just have to run wubi.exe and let it take care of everything.
Might want to get a fresh download.
[http://www.ubuntu.com/getubuntu/downloadmirrors]("http://www.ubuntu.com/getubuntu/downloadmirrors")
Scroll to the bottom of the page, and click 'Try Wubi Now'

Also might want to take a look at this
[http://ubuntuforums.org/showthread.php?t=875570&highlight=grldr]("http://ubuntuforums.org/showthread.php?t=875570&highlight=grldr")

Most likely someone has had the same problem, and found a solution. The forums are your friend, search search, then search some more.

---

### Post by matthewbrave on 2008-08-23
i did the same thing as you.

i extracted the iso using winrar and it never installed. i then burned a disc with the iso image and it installed.

---

### Post by Ryadt on 2008-08-23
> **Mr newb said:**
> so i can install it because the iso was like a winrar archive i still have the iso though

Just burn the iso to a disc and then reinstall.

---

### Post by Mr newb on 2008-08-23
i dont know how

---

### Post by Ryadt on 2008-08-23
Follow this link: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

Hope it helps you out ;)

---

### Post by unca.paka on 2008-08-23
If he's trying to install through Wubi(which is how I understand it) There shouldnt be any need to burn a cd. The Wubi installer will basically download the 8.04 iso, then install it from there.
Info here
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230]("https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230")

---

### Post by Mr newb on 2008-08-23
whenever i install from wubi i get an error when i boot

---

### Post by unca.paka on 2008-08-23
After 10min of searching the forums/google, I found the same problem your having with Wubi was caused by fragmented drives. The fix was to degfragment the drive, and scan for/fix disk errors while windows is running.

If you just want to give up on Wubi(which seems pretty shoddy to me) Theres plenty of guides on these forums that can get you to a dual-boot enviroment, even on the same drive.

---

### Post by Ryadt on 2008-08-23
Try this guide: [http://www.howtoforge.com/wubi_ubuntu_on_windows](http://www.howtoforge.com/wubi_ubuntu_on_windows)

---

### Post by Mr newb on 2008-08-23
I HAVE NO IDEA WHAT YOU GUYS ARE TALKING ABOUT:confused:

You guys are just saying random things I need a solution, all I need is that when I try to install ubuntu with wubi I get an error when I boot and when I try to boot ubuntu from a cd it doesnt boot.
I just need a solution and I'd appreciat some help

---

### Post by Ryadt on 2008-08-23
1. Can you post the error message you are getting.

2. Check your cd for any errors.

3. We are doing our best to help.

---

### Post by Mr newb on 2008-08-23
here is my error message whenever I boot ubuntu after installing it with wubi, and sorry I just have no idea what is wrong


Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart.

---

### Post by Mr newb on 2008-08-23
btw i think my cd isnt working because I dont have a clue how to make a boot cd, and the tutorial didnt really help

---

### Post by unca.paka on 2008-08-23
Alright, first off, defragment your hard drive. Open My Computer, right-click on C:, click properties, click on Tools, then defragment. 
Alternatively: Click Start, Programs, Accessories, System Tools, Defragment.

After that, follow the link that Ryadt gave you a few posts up. That will walk you through installing Ubuntu using Wubi(windows based Ubuntu installer).

If you still get the same error your getting after doing those things. Then theres another problem. From what I've found, it could be some sort of drive encryption that HP is using on your computer. But we'll deal with that after you follow the steps in this post, and the link above.

We are trying to help, and have posted many links which carry solutions to this problem.

---

### Post by CarlosNYB on 2008-08-23
Posting your errors may help.

Posting the steps you took to install with wubi may  help -- did you defragment first, how did you run wubi, etc.

---

### Post by Mr newb on 2008-08-23
i am such an idoit i have been refreshing page 2 finding no more answers when there was a page 3! thank you i will try defragmentation and tell you whethere it works or not

---

### Post by Mr newb on 2008-08-23
I am defragmenting now I will report back when its done

---

### Post by Sef on 2008-08-23
Please do not have two separate posts on the same problem.

---

### Post by Mr newb on 2008-08-24
hi I have defragmented my hard drive i still get the error:
Try (hd0,0): FAT16: no GRLDR
Try (hd0,1): NTFS5: 3
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null
Error: cannot find GRLDR in all drive. CTRL+ALT+DEL to restart.



After installed ubuntu with wubi,

any ideas what the problem is?

I appreciate your help

---

### Post by unca.paka on 2008-08-24
By any chance, when you installed w/Wubi, did you have a choice between FAT16 and NTFS? If so, the problem might be that you installed to FAT16, which your NTFS formatted drive will not like.

If thats the case, reinstall again, but choose NTFS.

---

### Post by tinybit on 2008-08-26
> 
Try (hd0,1): NTFS5: 3


This shows a possible bug in the ntfs boot sectors of grub4dos. If you are using wubi, the error message about fat16 should read: No WUBILDR

Which grub4dos/wubi version are you using?

BTW, your hard drive has an FAT16 partition. Its ID byte can be set to DE (hexa) or such by the manufacturer, but it is really a FAT16 partition. If you can by any means place grldr/wubildr into this partition, then your grldr/wubildr can be started normally.

---

