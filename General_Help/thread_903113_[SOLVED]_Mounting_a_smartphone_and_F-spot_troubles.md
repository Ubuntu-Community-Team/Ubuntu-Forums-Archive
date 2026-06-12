---
title: "[SOLVED] Mounting a smartphone and F-spot troubles"
date: 2008-08-27
forum: General Help
---

### Post by Kain000 on 2008-08-27
Hey everyone, 
I've finally found a viable solution for mounting my windows mobile pocket pc as a volume in ubuntu, so as to be able to transfer songs and audio books etc.  
Using the ubuntu wiki page about just this I am using a program called WM5torage to make the flash card in my phone look like any usb Flash drive.    Problem is that every time I plug my phone in, as Ubuntu mounts the volume, F-spot starts and  tries to import my photos from the phone, however in doing so creates some sort of memory leak and uses arround 95-99% of the system's memory.  (thank you conky) I can force quit (given the time) and things will run smoothly after that, but it's a real pain having to let the system catch up with the commands.  If let to sit and use memory F-spot will eventually load with an error saying that it cannot import the photos because the deice is out of memory.     

So I want to stop F-spot form auto running when I connect the phone, and thought that I had done so under System>Preferances>Remoable devices and media where I unchecked the box that allowed F-spot to run when a camera was pluged in.  While I was at it I disabled all other devices form auto running.  
F-spot still starts each time and I cant find anything to change withen F-spot itself.    

Any Ideas?

---

### Post by Rhubarb on 2008-08-28
You need to change this from within nautilus:
Places --> Home
Then, Edit --> Preferences, select the Media tab
Then change the Photos combo box into something you prefer, like "Do Nothing" or "Open Folder".

---

### Post by Kain000 on 2008-08-28
Thanks a lot, that solves a HUGE headache

---

