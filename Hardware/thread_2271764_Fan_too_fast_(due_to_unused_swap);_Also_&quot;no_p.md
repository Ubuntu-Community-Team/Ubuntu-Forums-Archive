---
title: "Fan too fast (due to unused swap?); Also &quot;no pwm-capable modules&quot;"
date: 2015-04-01
forum: Hardware
---

### Post by Stannis_King on 2015-04-01
I was running Ubuntu 14.10 for a while without any (fan related) problems. The fan was very quiet and would blow slightly when e.g. viewing HD videos etc. Then I had to reinstall Ubuntu due to a different problem. After the reinstall, the fan would speed and noisy up even when scrolling through a long text faster. For whatever reason, it turns out that the new install of Ubuntu wasn't recognizing the swap partition. I added the swap partition UUID to the /etc/fstab, and the problems with the fan stopped. The System Monitor indicated that the swap was being used.

I don't really know if this caused the fan to not speed up unnecessarily, but the fan behaviour reverted back to the pre-install state. It would only speed up and not too loudly with e.g. viewing long HD videos on the internet.

Then I had to reinstall Windows XP (it's dual boot). This fudged up grub, which I corrected via boot-repair.

Now, the problem with the fan is back. It speeds up when (I think) it shouldn't (e.g. it speeds up rapidly for a few seconds at a time while I'm typing this and I have only Firefox open with a few text-only tabs). After the boot-repair, Ubuntu didn't recognize the swap partition, so I reformatted it as swap and updated fstab. It does recognize it now, but it barely ever uses more than 0 of it. The problem with the fan persists.

I have no idea if any of this is related, i.e. if there is any connection between swap and fan speed, or if the problem is something completely unrelated (the only significant thing I remember doing at the same time as reinstalling Windows and boot-repairing, was that I installed Wine and uninstalled it.

I'm still running 14.10 and, for reference, the tasks which speed up the fan in Ubuntu significantly, have barely any impact on the fan in XP, while the temperatures differ insignificantly.

I'm using Compaq 6910p laptop, with 2GB RAM and Intel Core Duo CPU T7500 @ 2.20GHz × 2 processor.

When I follow [this guide]("http://askubuntu.com/a/46135/329762") on how to control fan speed, I get "no pwm-capable modules" error.

So, what caused by fan to start running faster much more often than it did up until a few days ago (this isn't a gradual over-time increase, but a sudden increase starting after the grub repairs), and how can I reverse it or slow it down?

---

### Post by weatherman2 on 2015-04-01
Swap space in Linux is "overflow" for when your system runs out of real RAM and needs to "swap" some other process in memory to free up RAM for something new.  So when you do normal things, normally little or no swap space at all is used. 

If you open a lot of windows or software that uses a lot of RAM (say open a huge picture in GIMP and try to edit it), you start swapping a lot and slow the computer down.  That can make the CPU work harder, which will cause it to heat up, which will cause the fan to come on more often.

But I know, that isn't what you are describing.   To answer one question: no, "extra swap space" can't cause the fan to come on more than necessary for any reason I can think of.

Even though you say the fan doesn't come on like that in XP, two things to consider:

1.  Enter your BIOS Setup and check the settings for both the fan and for "Intel Speed Step" if anyway.  Make sure the fan is set for "automatic" or something like that.   Also, make sure "Intel Speed Step" is ENABLED, not disabled, because that lets the CPU slow down to save power when idle, and that can have a big impact on how hot it gets and how much the fan comes on.

2. Any laptop that old, in my experience, is probably dirty inside and should have the CPU fan and heat sink cleaned out.  I've cleaned a number of them, and the difference in heat is amazing if you find a lot of dirt/dust/hair in there.  If it gets too hot, the CPU may "throttle" (slow it way down to cool it), which would make the laptop sluggish, or it could even shut off randomly.  So it's important to clean out the heat sink in there after a few years.

Getting to the heat sink and fan can be tricky.  I googled your model; here is a YouTube video that shows how to replace the fan (not that you need to, but it shows you how to get to the fan/heat sink area):

[https://www.youtube.com/watch?v=gaD9NxQnG8E](https://www.youtube.com/watch?v=gaD9NxQnG8E)

That copper piece of metal is the heat sink.  Those fins on the left can clog with dust/dirt, so removing the heat sink and cleaning it out can make a huge difference in cooling.

---

### Post by Stannis_King on 2015-04-01
I've cleaned the fan about a month or so ago.

Before I read your reply, I did two things. First, instead of swap being identified by UUID in fstab, I replaced UUID with the partition location (/dev/sda3 in my case). I believe this is how the fstab was set up before, when there were no problems with the fan. Second, I changed swappiness to 100. Now, the fan is back to its old ways. It's much quieter. (It's possible that I have done something else beside this by following some instructions on the net, but I really doubt that it accomplished anything.)

Why do I think swap affects fan speed? My logic is the following (and bear in mind that my knowledge of computers is very limited, especially when it comes to hardware). Hard disk and RAM are two different things, meaning if the hard disk is used more (via swap), the RAM will be used less, and thus the generated heat will be more evenly distributed across the laptop (by swap taking away some tasks from RAM, the hard disk will "take away" some heat from RAM, too). This heat distribution may not decrease the (overall) heat by much, but it might be just enough to not exceed the temperature threshold required for the fan to speed up. I don't know if that makes any sense, but my fan is quite again, so I'll refrain from doing anything you suggested unless the problem resurfaces.

Thanks for the advice, though!

---

