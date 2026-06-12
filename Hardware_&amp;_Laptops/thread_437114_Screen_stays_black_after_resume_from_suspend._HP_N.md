---
title: "Screen stays black after resume from suspend. HP NC8230"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by khughes on 2007-05-08
Hello everyone,

I have researched this issue alot and found other postings but I have a semi different issue that I am hoping someone can help me with.

First of all I am running an HP NC8230 with and ATI x600 card. I have feisty fawn (clean install) and I am running the open source ATI driver. My problem is that every time I suspend the computer, when it comes back it looks like the computer starts up by the status of the LED's, but my screen stays black.

I actually got this issue resolved by using the fglrx driver and following the suggestions from this post ([http://ubuntuforums.org/showthread.php?t=303718&highlight=ati+suspend]("http://ubuntuforums.org/showthread.php?t=303718&highlight=ati+suspend")) telling  me to do this:

Edit "/etc/default/acpi-support" and change the following lines:
```
MODULES_WHITELIST="fglrx"
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true
```

But then I had a new problem. I want to be able to run aiglx & beryl full time as well as be able suspend and resume. I just cant seem to get the beryl working when I am using fglrx driver, but it works flawlessly with the open source driver. The major change that seems to make this resolution work for me is the line "MODULES_WHITELIST="fglrx". Since I am not wanting to use fglrx I cant resume, and I dont know what to put in place of that. So does anyone know how I can modify the resolution above to work with the open source driver instead of fglrx.

---

### Post by khughes on 2007-05-08
Anyone?

---

### Post by khughes on 2007-05-09
Ok, I know there are alot of posts coming in and in 9 hours I am already on the 3rd page, but come on....40+ views and nobody has anything to say? :(

---

### Post by DagMan on 2007-05-09
I have differant graphics.  I did have a problem with resuming  into a blank screen though.   I think the fix was to stop /etc/acpi/screenblank.sh from running on suspend, but I don't remember if this was specifically it or something else related to the monitor.  Maybe it was something called by /etc/acpi/sleep.sh or one of the scripts in /etc/acpi/suspend.d

It might very well not be your problem but I'll have a look and see if I can figure out what I had done.

Edit: Yeah I don't remember now and I think I might have very well moved a script and have now lost it after shuffling some data around and making a mistake during the process.  Perhaps though, if you want to be very daring and want to see if something is in there that duplicates the problem, you can do something like running the scripts in /etc/acpi one by one to see if one screws everything up.  It's a kind of unsafe way of doing it but if all else fails and you want ot have a look... It's how I found my problem however I had a fresh install and wasn't concerned about losing data at the time.

---

### Post by misfitpierce on 2007-05-09
I have a compaq V2508 with ATI 200M and am having no problems with suspend and resume.... I have seen alot of posts about suspend problems though... Maybe they'll fix with an update. :)

BUMP for Khughes

---

### Post by DagMan on 2007-05-09
just ran accross this [http://ubuntuforums.org/showthread.php?t=434718](http://ubuntuforums.org/showthread.php?t=434718)

---

### Post by khughes on 2007-05-09
Yeah, I read that post and didnt try it, but I have it on my list. I read alot of other postings as well and thats what got me to this situation.

---

### Post by nehalem on 2007-07-01
Thanks for your post.  I can't help you with your issue but you helped me get resume working.

One question (for anyone), do you have sound on your speaker working?  I am having this problem:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21574](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/21574)

---

