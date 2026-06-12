---
title: "Ubuntu question"
date: 2008-08-23
forum: General Help
---

### Post by oib111 on 2008-08-23
I used to Dual Boot Windows and Ubuntu but if I ever shutdown or restarted directly from the computer (not using Windows shutdown/restart option, so physically shutting down/restarting) Ubuntu wouldn't be able to correctly access files and I would be directed to the bash shells. I want to install Ubuntu again, but I want to make it so that won't happen. Cuz sometimes I ***_NEED_*** to restart or shutdown physically, and I don't wanna reinstall Ubuntu every time :P

---

### Post by SPr on 2008-08-23
> (not using Windows shutdown/restart option, so physically shutting down/restarting)

Do you mean that you press the button on the front of the PC case? If it is causing problems with the file system then it is not a very wise thing to do. What are the conditions under which you have to hit the big button?

---

### Post by willc0de4food on 2008-08-23
usually when you do a hard reboot, such as what you described, you would still be able to boot linux, you just wouldn't have access to your NTFS partitions without booting windows up and having it clear the flags saying they weren't shut down properly (which it does automatically when it boots normally). so what happens when you do this hard reboot and you try to boot into linux? does it give an error or is your hdd just not detected or what happens? please give more details

---

### Post by Herman on 2008-08-23
:) Hello oib111,
> I used to Dual Boot Windows and Ubuntu but if I ever shutdown or restarted directly from the computer (not using Windows shutdown/restart option, so physically shutting down/restarting) Ubuntu wouldn't be able to correctly access files and I would be directed to the bash shells.There's no Windows shutdown/restart option in Ubuntu, but I am guessing you mean you were shutting down your computer wrong when you were running Ubuntu?

Shutting down your computer by using the big power switch or the reset switch or by pulling the cord out from the wall socket is no good for any operating system. It tends to damage the file system. Linux operating systems seem to be more vulnerable to this kind of damage.
 > I want to install Ubuntu again, but I want to make it so that won't happen.:( I can't help you with that, as far as I know that's just a fact of life when using a computer. If you install Ubuntu again, don't expect it to last very long unless you can change your habits.
> Cuz sometimes I ***_NEED_*** to restart or shutdown physically, and I don't wanna reinstall Ubuntu every time :P 	 Maybe I can help you by suggesting some less destructive ways for shutting down your computer when you're running Linux.
Probably it would be a good idea to print these out and keep them handy.

If your computer is partly frozen but your keyboard still works you may be able to switch to a 'tty' by pressing 'ctrl'+'alt'+'F1' (or any 'F' key from 1 to 6. 
That takes you to a black screen where you can log in at the prompt with you username and password. (Pressing 'F7' returns you to your Desktop again).****
Log in at the prompt and then issue the following command, `sudo shutdown -h now', or, 'sudo reboot -i'.
```
sudo shutdown -h now
```That should shut your computer down, if it takes a while just be patient and wait a few minutes.
Your computer might need time to close all your running processes and write any cached data to disk. If you want it to reboot, replace the 'h' (for 'halt', with 'r' for 'reboot', eg: 'sudo shutdown -h now'.

Another way to turn off your computer if your keyboard will work is with the the 'Raising Skinney Elephants' keyboard sequence, that trick always works.
Press
 'Ctrl'+'Alt'+'**r**' and then 'Ctrl'+'Alt'+'**s**' and then 'Ctrl'+'Alt'+'**e**' and then 'Ctrl'+'Alt'+'**i'** and then 'Ctrl'+'Alt'+'**u**' and and then 'Ctrl'+'Alt'+'**b**'.
Read this great link from 'Tips For Linux Explorers' links: [Skinny Elephants ( if all else fails )]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html")

If the computer is part of a network another way to shut it down is to log in from a nearby computer on the same network and shut it down remotely. See also [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").
This should work even if the frozen computer has lost the use of it's keyboard as well as it's mouse.
If the computer that is frozen has ssh server software installed and you know the IP address, users account details and password, (especially if it's your own computer), you can just ssh into it and shut it down, use the same commands already mentioned.
```
ssh herman@192.168.0.234
```
```
sudo shutdown -h now
```
If none of those ideas help and you have no choice but to use the big OFF switch at least be sure to run a file system check from a Live CD or different operating system right away as soon as you can. [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

If you're willing to at least try to take care of your file systems then there's a good chance your Ubuntu operating system will last for a long time. 
If you don't care to try to look after things it will be just like anything else in life that you don't take care of, and it won't last very long.

I hope that will help you even if it isn't quite the answer you might have been hoping for.
Regards, Herman :)

---

### Post by carolinason on 2008-08-23
Take the advice here. physically shutting down the pc while it's running can cause a hard drive head crash making your hard drive a paper weight,

---

