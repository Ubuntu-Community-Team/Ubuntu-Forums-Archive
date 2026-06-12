---
title: "Ubuntu won't boot to login screen"
date: 2016-04-19
forum: Hardware
---

### Post by kakashi_12 on 2016-04-19
Ubuntu 14.04
Seems to be since a recent update (can't tell which one) that it won't boot. Had this exact problem before, and had just restored an older image of my OS and that fixed it. But now I'm back to square one. Anyone have an idea how to fix it to get past that update so I don't have to just keep restoring the old OS image anymore? Here is a description of the error below...

"Checking disk drives for errors"
"Errors were found while checking the disk drive for /."
"Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery"

When choosing "F":
"the disk drive for /tmp is not ready yet or not present."
Continue to wait or S to skip mounting. I wait awhile longer and it reboots. Then it boots into the OS properly.
So I basically have to boot it twice for it to work.

When I use Windows to check the partition/drive, it checks out fine, no errors. So couldn't possibly be hardware related.
How do I get fix or diagnose this?

---

### Post by QDR06VV9 on 2016-04-19
One possibility...it could be looking for Swap
have you looked at "free"
Also grub may have need for maintenance now...(restoring old images)  
See this: [http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted)
Good Luck

---

### Post by kakashi_12 on 2016-04-20
Thanks.
I don't use WUBI. I dual boot. Didn't find any of this code in Easy BCD. So I had to
1. shutdown, unplug Windows drive (to be on the safe side)
2. boot up to boot directly to Ubuntu, go through that booting twice thing (since it doesn't boot right the first time), then log in.
3. Applications, System Tools, Administration, Grub Customizer.
4. Right click the top Ubuntu entry, Edit.
5. Change the code as described in the url. Save, exit, reboot.

Basically changing some boot entry from read only to read write. Weird. Had to have been an update that caused that change. ??
Only made the first change of code. Didn't see anywhere in grub where I could make the second change of code
(linux   ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative} ro ${args})
^ that line, didn't see that anywhere.

So far it's working normal again. I'll give it a couple of reboots and couple of days to make sure it doesn't act up again.
Thank you.

---

### Post by QDR06VV9 on 2016-04-20
Nice i am glad it worked out for you..
I have had the same thing happen when restoring other images a few times(Don't have clue why?)
But when you are satisfied and happy with the solution would you mark the thread solved as to help others.
Good Job and Kind Regards

---

### Post by kakashi_12 on 2016-04-21
No, this didn't happen as a result of restoring the OS image. It just happened (I'm guessing from some Ubuntu update?). I had to restore the OS image in the past to resolve this issue.... rather than just resolving it, as I have done now (above).
I was getting there.... Solved.
Thanks.

---

