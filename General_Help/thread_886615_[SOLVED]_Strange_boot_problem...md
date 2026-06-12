---
title: "[SOLVED] Strange boot problem.."
date: 2008-08-11
forum: General Help
---

### Post by Chronos6 on 2008-08-11
Hy!
I'm using Ubuntu almost a year now, and i had a problem with shutdown(had a black screen and the shutdown process stopped, if i pushed the power off button it gave me a beep and turned off after a few seconds - had to re-install). 
Now i have the following problem:
When i turning on my pc everything goes well(except the progress bar) and after the boot when the login screen would appear it freezes. Black screen and nothing, not even the num lock. 
And now comes the weird part: 
If i boot up in rescue mode, and exit immediately from rescue mode to resume the session, it boots up and the system is rock solid. 
I've tried everything what i could think of, please help me! 
I'm really pissed off. 
Thank you, i don know what logs to paste in, so just ask. 
Thanks, Chronos.
I have an nvidia mx440, 512ram, 2,7ghz celeron. Even the games are working while compiz-fusion is running.

---

### Post by cmnorton on 2008-08-11
This sounds like it could be graphics. 

When you exit from recovery mode, what are your screen settings?

It could be you need to reconfigure your X-server.

dpkg-reconfigure xserver-xorg

You can do this right after you boot into recovery mode. Answer all questions with the default answer, but pay close attention to the screen modes available and the driver being used. You may have to go with vga -- knowing you will never stay there permanently -- just to see if you can boot regularly.

I use the vesa driver with my laptop. The nvidia driver works fine, but not when the laptop is working in a KVM switch environment.

---

### Post by Chronos6 on 2008-08-12
I've figured it out that the boot process stops at a point and drops to root shell. With splash option to the kernel i cant see anything, so thats why it seems it is freezed.
So, how, and where can i get that line out from the boot process? init.d?
Thanks

---

### Post by cmnorton on 2008-08-12
It sounds like you need to correct what's causing you to drop to a root shell. 

You can specify no splash option to the kernel (one thing to try). I've been looking in these forums, and I know there are threads describing how to shut the splash option off I just have not found them yet.

---

### Post by Chronos6 on 2008-08-13
I've managed to turn off splash option, but my problem is how to find the line causing the dropping to shell every time the machine boots. 
I just deleted the splash option from the boot config file.
I tried to find with mc but its a lot of data to process. Any ideas where to look for this line?

---

### Post by cmnorton on 2008-08-13
This sounds like you are booting into recovery mode. You have about three seconds to press ESC at the grub menu to see how you are booting. 

The only other thing I can think of is to use 

find / -type f -exec grep "string" {} \; -print

Also, you can look into your logs, especially /var/log/kern.log as well as /var/log/syslog and /var/log/messages. Also look at the output of dmesg after you boot.

---

### Post by Chronos6 on 2008-08-13
No i'm afraid its not recovery mode, couse there i get a blue menu. And here i get a root prompt where i cant reach even midnight commander.
I will look after this later today.

---

### Post by az on 2008-08-13
When you power on, you can get to the grub menu (you may need to press escape to reveal it if it is not already shown).  When your selection is highlighted , press "e" to edit it.  Select the kernel line and press "e" again.  Hit end to get to the end of the line and delete the quiet and splash options.

Press enter and then "b" to boot.  You will then avoid the splash screen and will be shown verbose kernel output while booting.

---

### Post by Chronos6 on 2008-08-13
Ok, so i know what options i have, i know what the problem is, but dont know where is that *uckin line what gets a prompt right in the middle in the booting process.

The problem: 
The boot process is stopped at a point by a root shell. 

The probable solving:
Find the line in the boot process configs, but dont now where is that line..

---

### Post by az on 2008-08-13
At the prompt, type
dmesg
and the last few lines should tell you what the kernel was doing.

As well, getting rid of the "quiet" option in your kernel boot prompt will allow you to see more precisely at what point you are dropped to a shell.

The problem is not that a shell is being run by mistake;  you are dropped into a busybox shell when part of the initrd fails to do its job.

I don't think you are going to solve your problem by deleting things from init.d.  I think you need to find the problem and fix it, rather than just skipping that part of the init process.

Perhaps your initrd is improperly built.  What were you doing when you had to power down the computer forcibly?

---

### Post by Chronos6 on 2008-08-13
I dont remember powering off the pc before shutting it down, but i've found a similar thread:[URL="http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-8.04-will-not-go-to-login-screen-657755/#post3246078"]
http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-8.04-will-not-go-to-login-screen-657755/#post3246078[/URL]

I have the same output before the shell:
bash: no job control in this shell
bash: lesspipe: command not found
bash: command: command not found
bash: the: command not found
bash: dircolors: command not found
bash: command: command not found
bash: the: command not found

Any ideas?

---

### Post by Chronos6 on 2008-08-13
Ok, found the solution :D 
The problem was i took a hdd out from the pc, and the fsck system was still looking for it. 
I put one '#' in the fstab and viola! Everything is fine. 
I didn't saw the line above the errors...how silly is that...
Thanks for helping, and i hope that somebody will find this useful. Learn from my mistake. 
Take care, byya!

---

