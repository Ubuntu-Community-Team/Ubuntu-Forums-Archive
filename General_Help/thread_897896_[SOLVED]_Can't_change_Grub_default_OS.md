---
title: "[SOLVED] Can't change Grub default OS"
date: 2008-08-22
forum: General Help
---

### Post by abrahmm on 2008-08-22
Hey everyone,

I installed Ubuntu on a separate hard drive a few weeks ago to dual boot with my original Windows XP install. So far Grub has had Ubuntu as default and I have to manually choose XP when I start the computer.

I've been searching and trying to change the default OS booted but I can't get it to work. Simply editing the menu.lst file won't allow me to save it because I don't have permissions. But typing "sudo gedit /boot/grub/menu.lst" doesn't do anything. When I initially type it, it will ask for my sudo password. After I put the password in, nothing happens. It doesn't open up the menu.lst file. And if I type "sudo gedit /boot/grub/menu.lst" in again nothing happens, it just goes to the next line in the terminal. But, simply typing "gedit /boot/grub/menu.lst" will open the file, but I don't have permission to save it.

Anyone have any suggestions or help for me? I would greatly appreciate it. 
Thanks.

---

### Post by cmay on 2008-08-22
hi.
first i have never edited a grub menu file on linux so honest i do not know how to do it. but i have edited the sudoers file.
i think you can nay be get around it using something like
sudo nano :/name_of_file_ to_ edit
nano is a little terminal based editor 

hope it helps.

---

### Post by bubba_169 on 2008-08-22
You could try gksu instead of sudo? So it would be 'gksu gedit /boot/grub/menu.lst'

Alternatively there is a program in the repos called startupmanager that will help you configure grub options as well as your splash screens etc. Just search for it in synaptic

---

### Post by cmay on 2008-08-22
> You could try gksu instead of sudo? So it would be 'gksu gedit /boot/grub/menu.lst'
sounds like a good idea to try.
i am just used to nano as the terminal editor.
permissions would be the same i guess:)

---

### Post by drs305 on 2008-08-22
> **cmay said:**
> hi.
first i have never edited a grub menu file on linux so honest i do not know how to do it. but i have edited the sudoers file.
i think you can nay be get around it using something like
sudo nano :/name_of_file_ to_ edit
nano is a little terminal based editor 

hope it helps.

It sounds like you and abrahhm are a prime candidates for StartUp-Manager. It's a gui-based app to edit grub's menu list. You can set your default OS, how long you want to see the menu, how many kernels to view, and much more.

To install:
```
sudo apt-get install startupmanager
```

To run:
System, Administration, StartUp-Manager

Specifically, to set the default OS, go to the 'Boot Options' tab and select what you want in the "Default Operating System" window.

I wrote a tutorial about how to use it:
[URL="http://ubuntuforums.org/showthread.php?t=818177"]http://ubuntuforums.org/showthread.php?t=818177
[/URL]

---

### Post by abrahmm on 2008-08-22
> **bubba_169 said:**
> You could try gksu instead of sudo? So it would be 'gksu gedit /boot/grub/menu.lst'

Alternatively there is a program in the repos called startupmanager that will help you configure grub options as well as your splash screens etc. Just search for it in synaptic

Thank you for the help everyone. using gksu did the trick! thanks a lot!

---

### Post by Cheesehead on 2008-08-22
> **abrahmm said:**
> ...typing "sudo gedit /boot/grub/menu.lst" doesn't do anything. When I initially type it, it will ask for my sudo password. After I put the password in, nothing happens. It doesn't open up the menu.lst file. And if I type "sudo gedit /boot/grub/menu.lst" in again nothing happens, it just goes to the next line in the terminal. But, simply typing "gedit /boot/grub/menu.lst" will open the file, but I don't have permission to save it.

Your command is correct.
"sudo gedit /boot/grub/menu.lst" should be working. It's right.

Check for typos.
Even with a typo, 'sudo gedit any_file' should open *something*, even if just a blank page, or generate *some* system response.

Check sudo.
Does your sudo work properly for other commands?

Check your logs.
Your syslog and auth log should show the sudo use, and the command, and the result.

---

### Post by abrahmm on 2008-08-22
> **Cheesehead said:**
> Your command is correct.
"sudo gedit /boot/grub/menu.lst" should be working. It's right.

Check for typos.
Even with a typo, 'sudo gedit any_file' should open *something*, even if just a blank page, or generate *some* system response.

Check sudo.
Does your sudo work properly for other commands?

Check your logs.
Your syslog and auth log should show the sudo use, and the command, and the result.

It's strange, I had trouble initially with gksu but now both gksu and sudo work after I restarted. Not sure what the problem was but both seem to be working now /shrug. 

Thanks for the help guys.

---

