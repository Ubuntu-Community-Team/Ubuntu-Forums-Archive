---
title: "Dell M1530 Keeps Freezing"
date: 2008-10-23
forum: Hardware
---

### Post by patrikh20 on 2008-10-23
I am running intrepid with the most current updates. My problem is that the computer freezes after booting up and sitting for few minuites. Sometimes even a few seconds. It started happening a week or so ago, but would usually just freeze when the screen saver tried to load or when it was left idle for a long period of time. Now as soon as I boot up it freezes with a min or two. There was a kernel update i think 2 days ago. Not sure if that has anything to do with it, but this sucks. I have to boot into my crappy vista partition to use my computer. Also when it freezes the caps lock and num lock lights start blinking.

---

### Post by easy_target on 2008-10-24
I just updated from hardy few minutes ago and have the same problem. After a few seconds it freezes and the Caps Lock and Scroll lock leds keep blinking. 
Any ideas?
BTW if I log in root mode I can access it but keyboard and mouse won't work.

---

### Post by easy_target on 2008-10-24
Okay looked into /var/log/kern.log and found that the wireless card might be causing a kernel problem. It wasn't in hardy though. The wireless card is a D-Link Airplus DWL-520+.

Here are the sections that I think are pertinent, although I have no idea of what that means.

> Oct 23 11:11:06 Family kernel: [ 5347.014482] wlan0: peer 00:18:39:47:6B:88: incompatible basic rates (AP requests 0x026F, we have 0x0127). Considering anyway...
Oct 23 11:11:06 Family kernel: [ 5347.019700] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
Oct 23 11:11:20 Family kernel: [ 5361.006987] wlan0: tx error 0x20, buf 04! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Oct 23 11:11:20 Family kernel: [ 5361.007046] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
Oct 23 11:11:20 Family kernel: [ 5361.007054] wlan0: tx error 0x20, buf 07! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Oct 23 17:55:52 Family kernel: [29605.637406] wlan0: tx error 0x20, buf 00!
Oct 23 17:55:52 Family kernel: [29605.637422] wlan0: tx error 0x20, buf 01!
Oct 23 17:55:52 Family kernel: [29605.637429] wlan0: tx error 0x20, buf 02!
Oct 23 17:55:52 Family kernel: [29605.637438] wlan0: tx error 0x20, buf 03!
Oct 23 17:55:52 Family kernel: [29605.638763] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
Oct 23 17:55:52 Family kernel: [29605.638772] disabling above message until next recalib
Oct 23 17:56:01 Family kernel: [29614.604277] wlan0: tx error 0x20, buf 04!
Oct 23 17:56:01 Family kernel: [29614.604290] wlan0: tx error 0x20, buf 05!
Oct 23 17:56:01 Family kernel: [29614.604297] wlan0: tx error 0x20, buf 06!
Oct 23 17:56:01 Family kernel: [29614.604308] wlan0: tx error 0x20, buf 07!
Oct 23 17:56:11 Family kernel: [29624.590682] wlan0: tx error 0x20, buf 08!
Oct 23 17:56:11 Family kernel: [29624.590695] wlan0: tx error 0x20, buf 09!
Oct 23 17:56:11 Family kernel: [29624.590702] wlan0: tx error 0x20, buf 10!
Oct 23 17:56:11 Family kernel: [29624.590711] wlan0: tx error 0x20, buf 11!
Oct 23 17:56:18 Family kernel: [29631.726248] wlan0: peer 00:18:39:47:6B:88: incompatible basic rates (AP requests 0x026F, we have 0x0127). Considering anyway...
Oct 23 17:56:22 Family kernel: [29635.726854] wlan0: tx error 0x20, buf 12!
Oct 23 17:56:22 Family kernel: [29635.726869] wlan0: tx error 0x20, buf 13!
Oct 23 17:56:22 Family kernel: [29635.726877] wlan0: tx error 0x20, buf 14!
Oct 23 17:56:22 Family kernel: [29635.726887] wlan0: tx error 0x20, buf 15!
Oct 23 17:56:32 Family kernel: [29645.714963] wlan0: tx error 0x20, buf 00!
Oct 23 17:56:32 Family kernel: [29645.714977] wlan0: tx error 0x20, buf 01!
Oct 23 17:56:32 Family kernel: [29645.714984] wlan0: tx error 0x20, buf 02!
Oct 23 17:56:32 Family kernel: [29645.714993] wlan0: tx error 0x20, buf 03!
Oct 23 17:56:44 Family kernel: [29657.429324] wlan0: peer 00:18:39:47:6B:88: incompatible basic rates (AP requests 0x026F, we have 0x0127). Considering anyway...

And pretty much repeats itself a lot. This is not the sequence found in the file but I think it is pretty representative of what you see in there.
Is this a bug or a "feature"?

---

### Post by easy_target on 2008-10-26
I had no luck trying to make it work and I removed the wireless card and Ubuntu works again. Any ideas, please?

---

### Post by Pixcalcis on 2008-11-19
ugg same here on a thinkpad r60...though it does it very randomly. Sometimes it will freeze within a minute or two of boot and other times it can be a long time....and my caps lock key is flashing. I havent found it to have a relationship with any program i click on or anything. It seems very random...

---

### Post by wolterh on 2009-02-05
Well, this happens to me too. It seems that it is that wireless card issue, because the last time I had it was just when my computer was connecting to the network.

I guess that the solution might be that the ubuntu developers make the kernel abort any trial of connection if there is an error, instead of letting the machine freeze. Now, I don't know very much about how does this hardware errors work, but thats just a wild guess on how to solve the problem.

---

### Post by JibStyle on 2009-03-29
I'm having the exact same problem on my M1530 with intrepid 32bit.

Has anyone ever found a solution?

Thanks,
Tom

---

### Post by wolterh on 2009-03-29
Yes, I finally found a solution, but i forgot to post it here because I was testing it for some weeks. You just have to compile the latest wireless drivers, you can get them in [Linux Wireless]("http://linuxwireless.org"). They will link you to [this]("http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2") tarball, which gets updated on a daily basis, but please visit the website so you can get instructions.

When I installed it I got a kernel panic when running [$ sudo make unload]. After that, I booted with recovery mode and unloaded and loaded the new modules. Maybe you will get a different result if you go right away and run [$ sudo make load] instead. Anyway, read the README/INSTALL files that come within the tarball.

---

### Post by KevNice on 2009-03-31
I have the same problem.

I wanna try this solution but how do I check which wireless card I've got? I know it's an Intel but I don't remember the command to check the model number.

---

### Post by wolterh on 2009-03-31
I would tell you to run [$ lspci] but as you have the same machine I have, I bet we have the same wireless card. Anyway, you don't need to know which card do you have to try out the solution. The solution contains drivers for all wireless cards. They are installed automatically.

---

### Post by wolterh on 2009-04-05
However, I invite you all, Dell XPS M1530 users to join the group I list in my signature. My purpose is to maintain the community of us, this luxurious laptop's users, informed and with the capability of letting others know about how you solve your problems, etc.

I do not post this with any propaganda intentions, but to help the community. Consider this one of the many sand grains I've apported and will apport in the future to the ubuntu users. Moreover, I encourage anyone who has a different computer to go on and create a group for it.

---

### Post by jespdj on 2009-04-05
Have a look at my page: [http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

I have an Intel 4965 AGN WiFi card in my M1530 and it works fine out-of-the-box, never had any problems with it.

---

### Post by wolterh on 2009-04-05
Oh Jesper, its an honor even to see you in here, the ubuntu forums. I read your page and because of you, I was able to use my touchpad (because of the nomux fix). That's very lucky of you, to have never had a kernel panic or anything that made your caps and num lock blink repeatedly. Anyhow, I was just linking you, Dell XPS M1530, to the community I want to form. Again, Jesper, it would be an honor if you joined the group.

---

### Post by jespdj on 2009-04-07
Ok, joined the group... ;)

By the way, I tried Ubuntu 9.04 Beta on my M1530, and the touchpad seems to work there without the fix that was necessary for Ubuntu 8.04 and 8.10.

---

