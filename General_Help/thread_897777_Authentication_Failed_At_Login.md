---
title: "Authentication Failed At Login"
date: 2008-08-22
forum: General Help
---

### Post by eatdirt001 on 2008-08-22
I was having a problem where the keyring prompt kept popping up after every login so I found and followed some directions here:

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

When I restarted my laptop, an "Authentication Failed" message popped up. I don't even get a chance to type in the username and the popup won't go away. After some searching I found this, which seems to be the solution to my problem:

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4](http://ubuntuforums.org/showpost.php?p=3605925&postcount=4)

However, I don't understand where and how I am supposed to enter that code when I can't even get past the login page and what it means to  "comment the line". When I start up my laptop I am able to get to the menu that has the following lists:

Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, memtest86*

I've only started using Ubuntu for less than a month so if anyone has the the solution, please be specific about the instructions. By the way, my laptop is a hp dv2911us.

---

### Post by LateNiteTV on 2008-08-22
1. Boot your Linux box and start hitting 'Esc' until you get the GRUB menu. The GRUB menu passes by quickly. 

2. Select a boot image from the menu then press 'e' to edit. 

3. Select the Kernel line and press 'e' to edit. It should look something like this: 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
Edit the line to get rid of quiet and splash and add 'single': 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro single
4. Then press enter. You will be returned to the menu. 

5. Press 'b' to boot with these new settings. 

If if appears to boot normally, but you see a message that says: 

   Give root password for maintenance
   (or type Control-D to continue):

From there you can edit gdm and comment out that line.

---

### Post by Victormd on 2008-08-22
> **eatdirt001 said:**
> I was having a problem where the keyring prompt kept popping up after every login

To avoid this, the easiest thing is to simply set the keyring password to blank (the keyring password can be different from your user password).

This will increase vulnerability, BUT, for anyone to get to your keyring, they'll need to know your user password, so you're still protected by your user password. If your keyring password is the same as your user password, the security level is the same as leaving the keyring password blank (someone please correct me if this is wrong).

---

### Post by eatdirt001 on 2008-08-22
> **LateNiteTV said:**
> 1. Boot your Linux box and start hitting 'Esc' until you get the GRUB menu. The GRUB menu passes by quickly. 

2. Select a boot image from the menu then press 'e' to edit. 

3. Select the Kernel line and press 'e' to edit. It should look something like this: 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
Edit the line to get rid of quiet and splash and add 'single': 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro single
4. Then press enter. You will be returned to the menu. 

5. Press 'b' to boot with these new settings. 

If if appears to boot normally, but you see a message that says: 

   Give root password for maintenance
   (or type Control-D to continue):

From there you can edit gdm and comment out that line.

Thanks for your quick reply. I followed your instructions but I never see the message "Give root password for maintenance".

What I did exactly after entering the GRUB menu:
 
1. Highlighted "Ubuntu 8.04.1, kernel 2.6.24-19-generic" and pressed "e". 
2. Highlighted "kernel /boot/umlinuz-2.6.24-19-generic root=UUID=10888c93-f681-44cf" and pressed "e". 
3. Then what I see is "<3-f681-44c5-8d92-133c62c61a1e ro quiet splash". I replaced "quiet splash" with "single" and pressed enter where I get brought back to menu. 
4. I press "b" and I see a string of numbers and words against a black screen.
5. I get brought to a "Recovery Menu" and has the following options: resume, dpkg, root, and xfix. When I click on resume, I get brought back to the login screen where the Authentication Failed message is still there.

What am I doing wrong?

---

### Post by LateNiteTV on 2008-08-22
choose "root" and tell me what happens.

---

### Post by dannyboy79 on 2008-08-22
> **LateNiteTV said:**
> 1. Boot your Linux box and start hitting 'Esc' until you get the GRUB menu. The GRUB menu passes by quickly. 

2. Select a boot image from the menu then press 'e' to edit. 

3. Select the Kernel line and press 'e' to edit. It should look something like this: 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro quiet splash
Edit the line to get rid of quiet and splash and add 'single': 

   kernel /vmlinuz-2.6.15-27-386 root=/dev/mapper/Ubuntu-root ro single
4. Then press enter. You will be returned to the menu. 

5. Press 'b' to boot with these new settings. 

If if appears to boot normally, but you see a message that says: 

   Give root password for maintenance
   (or type Control-D to continue):

From there you can edit gdm and comment out that line.
an FYI, there was no need to edit a kernel line as that's what the recovery mode kernel line does, it boots to root. so all he would had to do was chose the recovery mode kernel line and booted that instead of all that editing etc.

---

### Post by eatdirt001 on 2008-08-22
A black line appears at the bottom and says "root@name-laptop:~#".

---

### Post by LateNiteTV on 2008-08-22
now follow the directions from the second link in your original post.

---

### Post by eatdirt001 on 2008-08-22
Thank you guys for the help but my problem hasn't been solved yet. I've tried everything but it just doesn't work. I don't want to have to reformat my laptop. I hope someone out there has the solution to this.

---

### Post by jonnylinux on 2008-09-19
hey i had the same problem. I am new to the linux world as well.

the missing logic to this solution is that gedit only works for me in the gui not in the shell. So instead of editing the line of code, I removed the file gdm. But first I made a copy at another location so I could edit and restore it once I got back in to the gui. This is what I did

I followed the instructions of booting into recovery mode by hitting esc on power up.

Then I chose root. entered my password for root. Not sure what the defualt one is if you have not set one. 

Then locate the file gdm by using cd to navigate the directories untill are able to locate it by typing ls gdm . it should be at etc/pam.d/gdm

then use cp gdm /   to copy it to the top directory.

then use rm gdm     to remove it from etc/pam.d

once it is deleted, you should be able to type reboot

and login normal. now you can sudo gedit the file and restore it to the proper location.

I hope this kicks your ubuntu's ***?/ Hardy hardly, they should call this thing wimpy wino! Just kidding guys seriously its privative, lets make it rock.

---

### Post by mssever on 2008-09-19
> **jonnylinux said:**
> the missing logic to this solution is that gedit only works for me in the gui not in the shell. So instead of editing the line of code, I removed the file gdm. But first I made a copy at another location so I could edit and restore it once I got back in to the gui. This is what I didDeleting /etc/pam/gdm isn't such a good idea. You can use nano to edit it if you need to.

---

