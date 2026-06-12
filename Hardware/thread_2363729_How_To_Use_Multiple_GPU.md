---
title: "How To Use Multiple GPU"
date: 2017-06-13
forum: Hardware
---

### Post by davidallyn68 on 2017-06-13
Please help... I'm short of reinstalling Ubunutu, but want to know what I'm doing first...

**What I would like...**
I've been running Ubuntu 16.04 for a year with a single AMD Radeon GPU (my Gigabyte mobo doesn't have GPU on board) using the open source driver  -- all is bueno!  I would now like to upgrade to an AMD Radeon RX550, and keep my older Radeon as my animation-render-helper.  

Initially, I thought I might be able to connect both GPUs to my monitor and flip between them as I want to, but I don't it really "works" like that, so I've given that up.  But, I seemed to have worked myself into a corner and I'm not sure how to 1) get out of my predicament and 2) how to set my system up correctly.

**What I've done...**
I followed the instructions on the [AMD driver website]("https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx") downloaded and installed AMDGPU-PRO based on recommendation of both AMD drive site and Ubuntu docs.  I shutdown my computer, I installed the new GPU in the second PCI Express slot -- leaving the old GPU untouched.  I plugged the HDMI of the new GPU into the second slot in my monitor.  I then booted up my computer again.

Now, the OS will boot to the login, I will enter correct creds, and then it pops me right back to the login.  It just cycles.  There are some error messages, but they flash too fast to read them.

When this happened, I decided to remove the new GPU and get the old setup to work correctly.  I have yet to make that happen.

I tried 
1) Booting into recovery mode, using the "dpkg" option, and it completes successfully.
2) Booting into recovery mode, using the "failsafeX" option, and it gives me a dialogue that I can't interact with - there are options for checking drivers and such, but I can't click or select any others.
3) Booting into recovery mode, using the "fsck" option, and it completes successfully apparently without error.
4) Booting to login, CTRL+ALT+F1 to "hard" terminal, I login successfully but really don't know what to do next.[INDENT]a) I tried "startx" based off a forum, but it comes back with display variable not set.
b) I tried "unity --reset", but it comes back with display variable not set.[/INDENT]

To be honest I'm just poking in the dark now, and need someone who has gone through this before -- or at least how to do it the right way.  Interesting that there aren't a lot of forums that discuss Multiple GPU, so it leads me to believe people aren't really having issue and it's just me.

Any ideas on next steps??

---

### Post by Autodave on 2017-06-13
You cannot have more than one video card at a time. You need to remove one of them and leave it out.

Now, having said that, let me change or explain my answer a little more. **IF** you had 2 identical video cards, it is usually possible to have both of them installed. However, only one of them can be used to connect monitors to it, the other one must remain unconnected to any cables.  Doing this type of setup will result in faster operation of the connected card because the unconnected card's processor can still be used to share the load. It will not make you card twice as fast, but it will speed it up to a noticeable improvement. Usually. Again, the cards MUST be identical, not similar.

Figure out what card you are going to use, remove the other, and report back with what happens when you try to boot up the system.

---

### Post by davidallyn68 on 2017-06-13
Well... I took out the original GPU, put in my new Radeon RX550, rebooted as normal.

As for multiple GPUs, well I might have to do more research on that.

Thank you sir!

---

### Post by Autodave on 2017-06-14
You are quite welcome. Please remember to mark this thread as CLOSED.

---

