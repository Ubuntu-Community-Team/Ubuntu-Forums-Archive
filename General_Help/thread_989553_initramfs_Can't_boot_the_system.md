---
title: "initramfs: Can't boot the system?"
date: 2008-11-21
forum: General Help
---

### Post by eternalnewbee on 2008-11-21
Hi there.
Could anybody tell me what error nr 16 is?
On another computer (no internet connection) Ubuntu 8.10 won't startup anymore.
I'd see the orange bar go back and forth for a few seconds, and then the error message.

---

### Post by eternalnewbee on 2008-11-21
**Update:**
I tried booting from the cd. Got to *select language*, and suddenly:
Loading, please wait...
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6)
built-in.shell (ash)
Enter 'help' for a list of built-in commands,
(initramfs)
**Choosing Install Ubuntu**: Same result.

---

### Post by newbee70 on 2008-11-21
> **eternalnewbee said:**
> Hi there.
Could anybody tell me what error nr 16 is?
On another computer (no internet connection) Ubuntu 8.10 won't startup anymore.
I'd see the orange bar go back and forth for a few seconds, and then the error message.

* 16 : "Device string unrecognizable"

      This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.

---

### Post by eternalnewbee on 2008-11-21
> This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.
From newbee newbee: What does that mean?
Wild guess: The problem is Hardware related?

---

### Post by newbee70 on 2008-11-21
> **eternalnewbee said:**
> From newbee newbee: What does that mean?
Wild guess: The problem is Hardware related?


Here is a link that will add to your confusion.

[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

my suggestion, if you don't have a ton of apps loaded do a clean install.
probability of hardware problem questionable at this time.

---

### Post by eternalnewbee on 2008-11-21
> my suggestion, if you don't have a ton of apps loaded do a clean install.
probability of hardware problem questionable at this time.
It won't even let me do that.

---

### Post by newbee70 on 2008-11-21
> **eternalnewbee said:**
> It won't even let me do that.

It won't let you install from a cd. even if you power off the system?

Sorry about that I just read your second post.
have you tried to revert back to 8-04-1?

---

### Post by eternalnewbee on 2008-11-21
> have you tried to revert back to 8-04-1?
Why would I want to do that?
It had been running without a glitch for a month.

---

### Post by newbee70 on 2008-11-21
I'm sorry I'm not familiar with busybox.

 I'll have to let the guru's help you out.

---

### Post by Thor_MMVI on 2008-11-21
I'm getting the same "busybox" message. It's not like Feisty, when I first tried that. The machine I'm attempting to install Ubuntu 8.04.1 or 8.10 was initially formatted for XP. Fiesty Fox allowed me to format the drive, etc. I'm not even getting any sort of GUI except on the initial CD install screen with 8.04.1 or 8.10

---

### Post by bennachie on 2008-11-21
Try installing again from scratch from the LiveCD. This time, when the initial boot dialogue comes up, hit F6. You will be presented with a line of parameters. At the end of the line, add:

all_generic_ide floppy=off irqpoll

The dreaded busybox/initramfs problem has been raised many times in this forum, and quite a number of people have found the above solution works. No guarantees, though ...

---

### Post by eternalnewbee on 2008-11-21
It's like there's no Hard disk detected. Again, I feel this problem hasn't got anything to do with Ubuntu, but malfunctioning hardware. But I'm waiting for heavy weight advice, to try to get to the heart of the matter.

---

### Post by eternalnewbee on 2008-11-21
> all_generic_ide floppy=off irqpoll
What will happen after this is added?

---

### Post by bennachie on 2008-11-21
Just go ahead and ask for the OS to be installed (or, if you prefer, just run Ubuntu in test mode directly from the CD - you will have several options from which to choose, and the desktop on test mode will include the package needed to install the system properly in any case).

---

### Post by newbee70 on 2008-11-21
Can you run it from the live cd without installing?

---

### Post by eternalnewbee on 2008-11-21
> Just go ahead and ask for the OS to be installed (or, if you prefer, just run Ubuntu in test mode directly from the CD - you will have several options from which to choose, and the desktop on test mode will include the package needed to install the system properly in any case).
Gonna give it a try.
> Can you run it from the live cd without installing?
Nope.

---

### Post by eternalnewbee on 2008-11-21
> Try installing again from scratch from the LiveCD. This time, when the initial boot dialogue comes up, hit F6. You will be presented with a line of parameters. At the end of the line, add:

all_generic_ide floppy=off irqpoll
I'm afraid I won't be  able to try this out for the next couple of hours, as I'm not physically at the computer in question, and neither is there anyone there.
I'll keep you posted if and when I've made any progress though.

---

### Post by eternalnewbee on 2008-11-22
**Update:**
> Try installing again from scratch from the LiveCD. This time, when the initial boot dialogue comes up, hit F6. You will be presented with a line of parameters. At the end of the line, add:
When I hit F6, I was presented with four or five options, but nowhere could I add a line.
What I did after that, is I chose the option to boot from the first hard drive, and that worked!!!
So I had Ubuntu started up, but no internet (there isn't a connection available yet).
And I ejected The Ubuntu CD and rebooted, to check if I could...
And I couldn't.
So my conclusion is: If I want to start up the system, I need to do that using the Ubuntu CD. Otherwise it's a no go (with my limited expertise).
So there you go.

---

### Post by eternalnewbee on 2008-11-22
> all_generic_ide floppy=off irqpoll
OK. So I managed to add this line (overlooked it the first time) but to no avail.
What's more, booting from the Ubuntu CD is not possible anymore.
The last thing I can think of is downloading another iso, and see if it is then possible to boot, or install.
Any ideas are welcome.
Thanks.

---

### Post by eternalnewbee on 2008-11-22
I hope someone can help me out soon[-o<

---

### Post by eternalnewbee on 2008-11-23
Can someone tell me why I am not even able to install ubuntu. Instead get stuck with initramfs?

---

### Post by newbee70 on 2008-11-23
> **eternalnewbee said:**
> Can someone tell me why I am not even able to install ubuntu. Instead get stuck with initramfs?

Question:

Have you ran any hardware Diagnostics on your system?

if not here is a website that has a diagnostics cd for download.
it might help you determine / rule out the hardware.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

[http://www.ultimatebootcd.com/download.html](http://www.ultimatebootcd.com/download.html)

---

### Post by newbee70 on 2008-11-23
> **eternalnewbee said:**
> Can someone tell me why I am not even able to install ubuntu. Instead get stuck with initramfs?

Here is a link to an article on intramfs, it may help you understand what is going on.

[http://www.linuxdevices.com/articles/AT4017834659.html](http://www.linuxdevices.com/articles/AT4017834659.html)

but think on the bright side we are learning quite a bit about how linux operates.   :)

---

### Post by eternalnewbee on 2008-11-23
> but think on the bright side we are learning quite a bit about how linux operates
Yes, but looking on the dark side, it's my 60-year-old mother's machine. Not mine.

---

### Post by eternalnewbee on 2008-11-23
I need **caljohnsmith**.

---

### Post by eternalnewbee on 2008-11-24
**Latest update:**
OK. So I downloaded 8.10 again and booted from the CD.
Now I had an additional option: Fix broken system (I think...)
Error 16 again.
Finally, I really don"t know how I did it, I managed to start the installation.
I got to the part **finishing installation**, and **reboot** the system, and so I rebooted, and this is what I got:
Boot from (hd0,5) ext3      afc54a58-5ac0-49a7-875f-2447e45e2eab
Starting up...
Loading, please wait...
Gave up waiting for root device
Common problems:
Boot args (cat /proc/cmdline)
-Check rootdelay=(did the system wait long enough?)
-Check root= (did system wait for the right device?)
-Missing modules (cat /proc/modules;ls /dev)
ALERT! /dev/disk/by-uuid/afc54a58-5ac0-49a7-875f-2447e45e2eab does not exist. Dropping to a shell!
BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)

---

### Post by bapoumba on 2008-11-24
Moved to General help.

---

### Post by eternalnewbee on 2008-11-24
Thanks, Bapoumba.

---

### Post by eternalnewbee on 2008-11-25
Hi there.
I requested to move this thread from Absolute Beginner Talk, and bapoumda moved to General Help. I hope there's someone here who knows to fix this problem, with the **initramfs** message.

---

### Post by eternalnewbee on 2008-11-25
Anyone, please?...
(some words of comfort maybe;))

---

### Post by caljohnsmith on 2008-11-25
Hi Eternalnewbee, I read through your entire thread, and I'll be happy to try and help out since you asked :); but based on the erratic/inconsistent behavior you describe, it unfortunately sounds like you are experiencing a hardware problem as others have suggested. To start, can you run the "test memory" option from the main menu of the Live CD? Since you are having problems even booting your CDs, it doesn't sound like your HDD is the problem, or at least not the only problem. You mentioned that this is an older computer? If you can't run the memory test option from the Live CD, you could download and use the Ultimate Boot CD that newbee70 linked to, which has the same "memtest86+" program for testing the computer's RAM. Let me know if that turns up anything, and we can work from there if you want. :)

---

### Post by eternalnewbee on 2008-11-25
> Hi Eternalnewbee, I read through your entire thread, and I'll be happy to try and help out since you asked ; but based on the erratic/inconsistent behavior you describe, it unfortunately sounds like you are experiencing a hardware problem as others have suggested. To start, can you run the "test memory" option from the main menu of the Live CD? Since you are having problems even booting your CDs, it doesn't sound like your HDD is the problem, or at least not the only problem. You mentioned that this is an older computer? If you can't run the memory test option from the Live CD, you could download and use the Ultimate Boot CD that newbee70 linked to, which has the same "memtest86+" program for testing the computer's RAM. Let me know if that turns up anything, and we can work from there if you want. 
Finally!
Caljohnsmith. I do agree about it being a hardware issue. So my next question would be: how should I use the **Ultimate boot CD**? As it probably is a hardware  issue, how could the ultimate boot cd help in any way?

---

### Post by caljohnsmith on 2008-11-25
Go ahead and boot the Ultimate Boot CD, and then you should get a main menu looking like:

[IMG]http://www.ultimatebootcd.com/graphics/screenshot.gif[/IMG]

Choose the "Mainboard Tools", and under that category somewhere (I can't remember right now), there should be an option for running a memory test, or using "memtest86+". That's the program you're after. Give that a shot and let me know what the results are. :)

---

### Post by eternalnewbee on 2008-11-25
> Choose the "Mainboard Tools", and under that category somewhere (I can't remember right now), there should be an option for running a memory test, or using "memtest86+". That's the program you're after. Give that a shot and let me know what the results are. 
Wow! You're way ahead of me.
I'm not at the computer in question. This only complicates matters (I know)
> To start, can you run the "test memory" option from the main menu of the Live CD?
I did that already, yesterday, and eventually rebooted the system, after more than 13 hours of running the memory test. It had showed more than 900 errors, and was still running...
So I inserted the newly downloaded Ubuntu CD, and the rest is history.
> Go ahead and boot the Ultimate Boot CD, and then you should get a main menu looking like:



Choose the "Mainboard Tools", and under that category somewhere (I can't remember right now), there should be an option for running a memory test, or using "memtest86+". That's the program you're after. Give that a shot and let me know what the results
I will follow up on your advice and get back to you. Really appreciate you taking the time to help me out. Thanks

---

### Post by caljohnsmith on 2008-11-25
> **eternalnewbee said:**
> > To start, can you run the "test memory" option from the main menu of the Live CD? 
I did that already, yesterday, and eventually rebooted the system, after more than 13 hours of running the memory test. [COLOR="Red"]It had showed more than 900 errors[/COLOR], and was still running...
So I inserted the newly downloaded Ubuntu CD, and the rest is history.

I will follow up on your advice and get back to you. Really appreciate you taking the time to help me out. Thanks
Yikes :shock: 900 memory errors? Well I think it's safe to say that the RAM is at least part of the problem, if not the sole cause of all the problems. I suppose it's still possible that the RAM could be OK and its a problem with dirty connections or motherboard, but I think that's not likely. If it is just the RAM going bad, in a way that is good since RAM is so cheap now to replace. But didn't you say it was an old computer? If it is more than about 7-8 years old, I would recommend thinking about getting a new one in case that is an option. If the computer is too old, it may not be worth replacing the RAM since it is at a higher risk of having other hardware problems too. It's up to you of course, because I don't know if getting another computer is even an option. Anyway, let me know what you decide to do. :)

---

### Post by eternalnewbee on 2008-11-25
> But didn't you say it was an old computer?
That would actually be my mother:lolflag:
But seriously. No. As a matter of fact, my mom's computer is newer than mine (less than 3 years), but if it's just a question of RAM, that can easily be fixed. So the initramfs message (or error if you like) could be caused by too little RAM?

---

### Post by eternalnewbee on 2008-11-25
> I suppose it's still possible that the RAM could be OK and its a problem with dirty connections or motherboard
What do you mean by "dirty connections"?

---

### Post by eternalnewbee on 2008-11-25
I'm gonna have to call it a night now, caljohnsmith. Gotta get up early. But once again, glad you're helping me out. I'll keep you posted.

---

### Post by caljohnsmith on 2008-11-25
> **eternalnewbee said:**
> That would actually be my mother:lolflag:
My mistake, I should have read your previous post a little closer. :oops:
> **eternalnewbee said:**
> 
But seriously. No. As a matter of fact, my mom's computer is newer than mine (less than 3 years), but if it's just a question of RAM, that can easily be fixed. So the initramfs message (or error if you like) could be caused by too little RAM?
I don't know if too little RAM would cause the problem or not, but definitely having any type of memory errors at all can wreak havoc on anything you try and do with that computer. Having all those memory errors is not a good sign since it is a newer computer. I would try and run some programs on it that will detect the motherboard temperatures, because maybe that's also a problem; it might be overheating. Unfortunately though, the only programs I know of off-hand that detect motherboard temperatures are all Windows programs; I haven't yet researched what linux-equivalent programs there are for detecting motherboard temperatures, but I'm sure they must exist. 
[QUOTE=eternalnewbee]
What do you mean by "dirty connections"?
[/quote]
I was thinking more if it was an older computer that might possibly be an issue; but since it is a newer computer, before you replace the RAM, I would "re-seat" the RAM, i.e. pull it out and put it back in, just to make sure it's not a loose connection. After doing that run the memtest86+ program again, and if it still detects errors, then you're probably stuck with having to replace the RAM if you want to get the computer working again. Hopefully the RAM is the only problem, and not just a symptom of something worse. Let me know what you decide to do. :)

---

### Post by bapoumba on 2008-11-25
Thread title edited :)

---

### Post by eternalnewbee on 2008-11-25
> 
Thread title edited
Here I go, feeling spoiled again. Thanks bapoumba.

---

### Post by eternalnewbee on 2008-11-25
Good morning from Thailand.
> My mistake, I should have read your previous post a little closer
No problem.
> but since it is a newer computer, before you replace the RAM, I would "re-seat" the RAM, i.e. pull it out and put it back in, just to make sure it's not a loose connection.
I'm going to contact a guy I know who knows his way around in hardware and ask him to do this.
> After doing that run the memtest86+ program again, and if it still detects errors, then you're probably stuck with having to replace the RAM if you want to get the computer working again.
The last time I performed the memory test, it was still not done after about 13 hours, but I will run the test again.
Why should the RAM be replaced? Can I not just add more?

---

### Post by caljohnsmith on 2008-11-25
> **eternalnewbee said:**
> 
The last time I performed the memory test, it was still not done after about 13 hours, but I will run the test again.
Why should the RAM be replaced? Can I not just add more?
If I remember correctly, I think that memtest86+ program simply repeats its memory testing steps perpetually so that it never actually finishes; just watch the steps it goes through, and once you notice it going back to step 1, then you can stop it. Also, if memtest86+ reports any memory errors after reseating your RAM modules, that means most likely the RAM itself is dying, so you wouldn't want to keep it or simply add more memory. I don't know how many memory modules your mom's computer has, but if you're lucky, maybe only one of them is going bad so only one would need replacing. You can deduce which memory module has the problems if you write down the memory location of the error that the memtest86+ test reports. Let me know how it goes.

---

### Post by eternalnewbee on 2008-11-25
> if memtest86+ reports any memory errors after reseating your RAM modules, that means most likely the RAM itself is dying, so you wouldn't want to keep it or simply add more memory.
I understand.
> I don't know how many memory modules your mom's computer has, but if you're lucky, maybe only one of them is going bad so only one would need replacing. You can deduce which memory module has the problems if you write down the memory location of the error that the memtest86+ test reports. Let me know how it goes.
I think for 4 or 5 modules, not entirely sure, but I will write down the location if it comes up. Thanks caljohnsmith.

---

### Post by eternalnewbee on 2008-11-26
OK. This is what happened:
We took out the RAM, and put it back in again and started up the system. Voila! There it was. Perfect. So here I was, 5 minutes ago, replying to you about the success, when my mother called, 2 minutes ago, to tell me that everything had gone black. Nothing.
So I come to this conclusion: You were right about the RAM. It has to be replaced, right?

---

### Post by caljohnsmith on 2008-11-26
> **eternalnewbee said:**
> OK. This is what happened:
We took out the RAM, and put it back in again and started up the system. Voila! There it was. Perfect. So here I was, 5 minutes ago, replying to you about the success, when my mother called, 2 minutes ago, to tell me that everything had gone black. Nothing.
So I come to this conclusion: You were right about the RAM. It has to be replaced, right?
Did your mother run the memtest86+ on it again? If that test still gives a bunch of errors, then yes, I agree with you, sounds like it's time to replace the RAM. If she can though, have her write down the memory location of the errors, and she might only have to replace one memory module if she's lucky. How much RAM does that computer have? When you re-seated the memory modules, how many were there?

---

### Post by eternalnewbee on 2008-11-26
Hi caljohnsmith.
My mother can not run the memtest.
I will do it tomorrow, although I'm  feeling pessimistic about the outcome right now.
The original RAM is 512, and I added another 256. Thing is, the guy who helped me, first inserted only the 256 RAM, and got nothing but beeps.
But after reinserting the original 512 RAM, it started up alright.
I Still think you're right about the RAM dying. But I can only test this with new RAM. Tomorrow is another day. For  now, suffice it to say that when my mom starts up the computer, all she gets is a black screen. I'm sure now, that this is going to be solved, but I'd have to physically be at my mom's computer to make a (if any) difference. New update *coming soon* (Tinglish= Thai English)

---

### Post by caljohnsmith on 2008-11-26
Just a thought, but are you sure the 256 MB RAM module is the right type for the computer? I'm not familiar with all the different types of RAM, but there is DDR, DDR2, etc. I'm just wondering if maybe that is why the computer just beeped at you when you tried it. Anyway, good luck and keep me posted. :)

---

### Post by eternalnewbee on 2008-11-26
> Just a thought, but are you sure the 256 MB RAM module is the right type for the computer? I'm not familiar with all the different types of RAM, but there is DDR, DDR2, etc. I'm just wondering if maybe that is why the computer just beeped at you when you tried it. Anyway, good luck and keep me posted.
I'll check and see what type of RAM it is.
Good morning from Thailand.

---

### Post by eternalnewbee on 2008-11-27
Hi caljohnsmith.
OK. So my friend did the following: He unplugged the hard disk, and plugged it back in again. He said that he thought he should do that, because besides the fact that the screen was totally black, there was no system sound either. After that he cleaned the cpu fan, and cleaned the RAM card with an eraser (?). Then we booted the system. OK.
Everything is working again.
Rebooted the system several times and even shut it down for a couple of minutes. No problems.
I'd like to mark this thread as solved, but I think it's safer to wait for a couple of days, and see if any other issues, relating to this one arise.
Thanks again for your support.
One last thing: I still have to run the memory test, but I won't be able to do that until Monday. I'll let you know the outcome.
All your feedback is welcome, and if you ever decide to come to Thailand, you've got a friend. Just let me know.
Talk to you soon.
Bird. (that's my Thai nickname).;-)

---

### Post by caljohnsmith on 2008-11-28
Let's hope that your mother's computer continues to stay working and healthy, but I'll be interested in the results of the memory test. If I ever have a chance to visit Thailand, I will certainly let you know so we can get together for lunch or something. It's too bad the political scene in Thailand is so volatile right now; I hope you are safe where you are. Anyway, keep me posted on how events continue to unfold with your mother's computer. :)

---

### Post by eternalnewbee on 2008-11-28
> Let's hope that your mother's computer continues to stay working and healthy, but I'll be interested in the results of the memory test. If I ever have a chance to visit Thailand, I will certainly let you know so we can get together for lunch or something. It's too bad the political scene in Thailand is so volatile right now; I hope you are safe where you are. Anyway, keep me posted on how events continue to unfold with your mother's computer.
Thanks for your concern caljohnsmith.
I'll definitely let you know the results of the memory test.
And yes, Thailand isn't really a dream destination at the moment.
My brother is coming at the beginning of January...
He had already bought a ticket before the situation escalated.
Aanyways. The violance we're confronted with here is all from TV. Our daily lives continue as usual.
Update complete:smile:

---

### Post by eternalnewbee on 2008-12-01
Hi caljohnsmith.
I've run the memory test, and you're in for a surprise:

---

### Post by eternalnewbee on 2008-12-01
This one is clearer

---

### Post by caljohnsmith on 2008-12-01
That's a shame; still getting memory errors I see. I notice that all the errors are around 13-15 MB, so if your mother's original 512 MB memory module is in the first memory slot, then I'm fairly certain that means the 512 MB module is the failing one. I think she would be best off completely replacing that 512 MB module. I suppose the other 256 MB module would be just enough to just get by, but having more memory will certainly help her computer's performance. Good luck and let me know how it goes. :)

---

### Post by eternalnewbee on 2008-12-01
> That's a shame; still getting memory errors I see. I notice that all the errors are around 13-15 MB, so if your mother's original 512 MB memory module is in the first memory slot, then I'm fairly certain that means the 512 MB module is the failing one. I think she would be best off completely replacing that 512 MB module. I suppose the other 256 MB module would be just enough to just get by, but having more memory will certainly help her computer's performance. Good luck and let me know how it goes
Hi caljohnsmith.
Thanks for your reply.
So, I'll buy my mother new Ram for her birthday (that's 24 days from now), and run the memory test again.
> I suppose the other 256 MB module would be just enough to just get by
I thought you needed at least 384 MB to run Ubuntu...
Anyways, Everything's running fine now, but will update, after having installed new RAM.
Btw. when I install new RAM, and run the memory test again, and there are no errors, should I throw my old RAM away, or is it still usable?

---

### Post by caljohnsmith on 2008-12-01
> **eternalnewbee said:**
> 
Btw. when I install new RAM, and run the memory test again, and there are no errors, should I throw my old RAM away, or is it still usable?
Unfortunately, I don't think that failing 512 MB module will work in any computer, assuming your mother's problem is truly with the memory and not related to a motherboard issue or something else. Once you are sure her computer is running smooth with the new memory, my vote is definitely toss the old 512 MB, as it seems that is the troublemaker. :)

---

### Post by eternalnewbee on 2008-12-01
> Unfortunately, I don't think that failing 512 MB module will work in any computer, assuming your mother's problem is truly with the memory and not related to a motherboard issue or something else. Once you are sure her computer is running smooth with the new memory, my vote is definitely toss the old 512 MB, as it seems that is the troublemaker.
I understand. This may take a while, but I'll keep you posted.
Thanks, caljohnsmith.

---

