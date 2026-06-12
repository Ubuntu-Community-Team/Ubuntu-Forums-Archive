---
title: "help recovering deleted files, using Foremost/other way.."
date: 2008-09-20
forum: General Help
---

### Post by pizzaul on 2008-09-20
I am very new to linux, I just switched from vista to 8.04. Things were going fairly well until I managed to accidentally delete my documents folder I was trying to transfer from my old hard drive!

So. I switched my box off and put in a backup drive with a live ubuntu cd. Now I am trying to recover the data off of my old drive. 

I tried to download the program Foremost, [http://foremost.sourceforge.net](http://foremost.sourceforge.net). Using the terminal to download the package automatically didn't work (i assume because I'm running live) so I downloaded it manually. Now I don't know how to install it! Is it possible to install it on a live copy anyhow? If not... I found ways to search for txt documents, but it's pretty complicated for my level of linux know-how at the moment, and a lot of the documents are not .txt. 

Please help! There is a lot of very important information in that folder!

---

### Post by pizzaul on 2008-09-20
Just found this thread [http://ubuntuforums.org/showthread.php?t=679117](http://ubuntuforums.org/showthread.php?t=679117). Specifically I was interested in looking in /root/trash to see if my files were there, but I think I remember setting something so that deleted files do not go to /root/trash ?  Even so, I would like to try it.

...

Just tried looking in my root folder, but I didn't see anything. Could the files be hidden? If so, where do I find the setting to view hidden files?

...

Ok I just found this thread also, [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), which answers the question of whether foremost will or will not run on live... I got the package installed, but now I can't figure out how to launch the program.. Sigh. Using run application doesn't work, even if I check the 'run in terminal' option. What am I missing?

---

### Post by cariboo on 2008-09-20
If you are using this:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

page as a guide all the commands must be entered in a terminal. The terminal is located in Applications-->Accessories-->Terminal.

Jim

---

### Post by pizzaul on 2008-09-21
I know about the terminal, I am just not familiar with it yet. I am used to DOS, and have been using it for years, but I've only been using the terminal for about a week now, and hadn't planned on diving directly into it so soon. I was just trying to move files off an old HD and effed up somehow, so now I get a crash course. 

One thing I'm having problems with is that so many places offer code with no explanation for the different tags, so I'm blindly cut/pasting stuff in and getting errors, don't understand the error syntax, nor can I tweak my input because I do not know what I was typing in the first place!

I'm trying to work through the Foremost bit on the page [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery), and the code

sudo mount /dev/sdb1 /recovery
sudo mkdir /recovery/foremost

means... ? Sorry to be an absolute noob here, but I am confused. What are the /dev and /sdb1 roots? Are they the equivalent to the window's C:, D:, etc? if so, how specifically? are these two lines of code set up to begin recovering data from a live account, or from an installed copy of linux? At the moment I am trying to use Foremost and linux from a separate disk than the one with the deleted files, so does the above code still apply?

These are the types of things that are causing me problems at the moment. i'm gonna crack another cold one and hope someone clues me in :'(

---

### Post by pizzaul on 2008-09-21
I found [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php) which is answering a lot of my questions. Will dink around more, reply if progress is made...

---

