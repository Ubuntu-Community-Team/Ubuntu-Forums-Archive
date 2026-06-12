---
title: "Can not adjust brightness on Sony Vaio VGN series"
date: 2009-04-17
forum: Hardware
---

### Post by dungleonhart on 2009-04-17
Hi guys,
I've installed Ubuntu on my Sony Vaio laptop. Unfortunately, I can not adjust the brightness by using FN+F5 or F6.

Even when I use these code, it didn't work:
    sudo apt-get install spicctrl

    spicctrl -b 244
or 
    sudo chown system_username /proc/acpi/sony/brightness 
    echo "n" > /proc/acpi/sony/brightness

the error is "/proc/acpi/sony/brightness: No such file or directory"

So, if anyone use Ubuntu with Sony Vaio and have the /proc/acpi/sony folder, plz send it to me (Email: [email]dungleonhart[at]yahoo.com[/email]) or give me a tip to overcome this problem.

Thank you so much.

---

### Post by coffeecat on 2009-04-17
It's not a simple as someone mailing you a system folder, I'm afraid.

Some questions:

Which model number is your Vaio? How old is it? Most, if not all, are VGN-something now. Unfortunately, Sony use several different methods for controlling the Fn keys, depending on model. For my old VGN-FS series, I have to compile something quite different. For my new VGN-NS series, the Fn keys work out of the box with Ubuntu 8.10 and 9.04. I haven't tried 8.04.

Next question: which version of Ubuntu are you trying? If it's 8.04 or earlier, I suggest you try 8.10 or 9.04 (the release candidate is now available). With newer kernels, and hence more up-to-date drivers, these later releases might just work.

Where did you get the instructions from to configure spicctrl? If /proc/acpi/sony/brightness isn't there you may have made a mistake somewhere or omitted an important step.

Last comment: I suggest you edit your post and change your email address to dungleonhart AT yahoo DOT com. Humans can read that; bots can't - at least not yet, I hope. Be prepared to expect a deluge of spam if you publish your email address in bot-readable form like that.

---

### Post by dungleonhart on 2009-04-17
I really want to show my deepest gratitude toward you for your reply. Although it doesn't directly solve my problem, I did learn a lot from it.

1. I use Sony Vaio VGN-NR310E with Ubuntu 8.10 (i've updated the latest package)

2. The instructions below are from the thread [http://ubuntuforums.org/showthread.php?t=88611](http://ubuntuforums.org/showthread.php?t=88611)

3. I've just edited my email from @ to [at] (first time to hear about that :D)

Again, thank you very much.

---

### Post by coffeecat on 2009-04-18
I had a look at the thread you linked to. It was started over three years ago, so it may be that spicctrl was intended for earlier models of Sony Vaios. Iirc spicctrl didn't work on my older Vaio, and I had to use a more convoluted method. Interestingly, there is no /proc/acpi/sony/brightness in Jaunty on my newer Vaio (posting from there now), yet the Fn keys work out of the box for both brightness and sound.

I tried googling your model number but the only relevant thread on this forum is this one. :-| (Useful tip: if you want to search this forum, try googling - site:ubuntuforums.org *your search string*. Often better than the forum search.)

There was a thread on this forum a year or so ago where some developers (independent of Ubuntu I think) were researching this whole area of Sony Fn keys and invited Vaio owners to upload the results of a special hardware interrogation script they had posted. Their intention was to try to develop drivers for all the variety of Sony Fn keys. The thread went on for pages so they would have had some good material to work on. If I can find the thread again, I'll post it because it may give a link to the developers' website. Hopefully, they may have an installable package you could try out.

Another thought: the official release of Jaunty is on Thursday next week. Download yourself the desktop live CD, run it live and see if the Fn keys work. You never know. Or, if you're impatient, download the release candidate and try that. Not much is going to change between the final and the RC - just a few bug fixes hopefully.

Last idea: failing getting the Fn keys to work, have you tried right-clicking on a panel, selecting 'Add to Panel' and adding the Brightness applet? It's not as convenient as the Fn keys, but a must on a Vaio. If yours is anything like my two, it's far too bright at maximum setting. On my older Vaio, I've given up compiling all the stuff I needed to get the Fn keys work, and now I just use the brightness applet.

> **dungleonhart said:**
> deepest gratitude ... thank you very much.

My pleasure. We Vaio owners need to stick together. :wink:

---

### Post by leandromartinez98 on 2009-04-18
I have a Vaio VGN-NR11Z/S and the Fn keys for brightness started
working upon update to Jaunty-beta (9.04). I couldn't make them
work before that.

---

### Post by coffeecat on 2009-04-18
**dungleonhart**, the previous poster's experience with Jaunty is encouraging.

Anyway, I promised you a link. Here it is:

[Calling all Vaio owners]("http://ubuntuforums.org/showthread.php?t=465491")

It's a little older than I remembered and stops about 9 months ago. It may not be any help after all, but I see that the OP is still active on the forum, so he/she may have posted something more recently. That is if Jaunty doesn't cure the problem. :wink:

---

### Post by dungleonhart on 2009-04-18
I'm updating Ubuntu to the 9.04 RC version right now, and waiting for whether it would fix that bug or not. I will also read carefully the instructions from the link you gave me to get more knowledge about this problem.

I really think that I am so lucky to have an adviser like you, **coffeecat**. Therefore, I have no more thing to say but thank you very much again and again :D.

---

### Post by ZeroCool69 on 2009-05-28
Greetings fellow Vaio owners.

I've had some great progress recently solving some nagging Vaio issues such as sound, wireless, et al. But this screen brightness thing is dragging on.

I have a VGN-FW140D Running a dual-boot with Vista SP2 and Jaunty 9.04

Fn keys are not working to adjust brightness, and neither is adding the brightness applet to the panel. Fn + F2 to mute sound works so I know that there's just something that needs to be adjusted to make it over this hurdle.

Any similar issues/fixes? Thanks

---

### Post by gseaton on 2010-02-27
I just picked up a VAIO VPCF115FM (i7; 2/2010) and installed Ubuntu 9.10 64.  

The screen brightness keys don't work AND the brightness applet (panel -> right-click -> add to panel -> Brightness Applet) does not work either.

Any help would be appreciate.

Thanks.

---

### Post by gitano on 2010-03-10
hey i have the same VAIO VPCF115FM- i am not experiencing your problem- all the fn keys work, except for the magnifier -f9 and f10

my problem is the nvidia geforce 330m-  i am stuck at 800x 600

and also the built in speakers- i can only get sound using external speakers.


so, do you have full 1900x1080?

do your built in speakers work?


im running a clean install of 64 bit 9.10, alongside the original win 7.

by the way i have already sent this up using the system testing in system- administration, using launchpad.


any input would be appreciated.  i hope its just a matter of time- but today i was very intrigued to see your post, as it mentions nothing about video problems. thanks

---

### Post by bjaz on 2010-06-29
same question here for a japanese sony VAIO VGN FS21 model, running Ubuntu 10.04- 
i've been looking around but could find a clear answer as to wether or not it's possible to get the F2 to F7 keys working in Lucid on such an old model

thanks in advance

ben

---

