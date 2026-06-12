---
title: "Unknown source of sound, being played in the background"
date: 2009-03-04
forum: Hardware
---

### Post by gutsy_shrikant on 2009-03-04
I installed Ubuntu 8.10 recently. There is a constant sound that keeps coming at some intervals. It sounds like "ding diing diiing" or something like that.
Any idea what process might be responsible for this. I have several process running like pidgin, weather forecast and firefox. I dont think any of those is making this sound. 
Any help is much appreciated. 
thanks a lot.

---

### Post by theresonant on 2009-03-04
Don't know if this will be of any help, but here's a way to find out what processes might be doing this sound.

First, run this command in a terminal: 

ps -A > ~/Desktop/processes.txt

It will create a file on your desktop with the output of the command "ps -A", which shows all processes. Then log out, and log in using a different session (Options button on the lower left corner-> Select Session...) and select "Failsafe terminal". If it asks whether to make this session default, say no, since it's just for this time. Enter your username and password and you'll see only a white terminal window on the screen. Wait a while, and if you don't hear any weird sound, it means that the process that made it is not running. Even if you do hear it, continue as this:

You won't be able to go online very easy, so rather write the command on a piece of paper or something. Run the previous command in the white terminal, just that instead of "processes.txt" write "processes2.txt", like this:

ps -A > ~/Desktop/processes2.txt

Then type "exit" and hit enter. You should be back to your login screen. Enter your username and password again. Now with your regular desktop, open a terminal and run this:

diff ~/Desktop/processes.txt ~/Desktop/processes2.txt

Please copy-paste here what that command outputs.
If you don't get to your normal desktop, just go to Options again and select "Gnome", "KDE", or what you were using before.

---

