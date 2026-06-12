---
title: "making file and printer server"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by drudogg on 2009-11-07
i want to build a "server" out of a desktop build of either ubuntu or crunchbang, have not decided yet, but CB is lighter and faster so i am leanig that way...

anyway i want to know what packages i need to look for to get print/file/remote login support. i want to share files as securly as possible, and i want to be able to access those files from any internet connection as well as from win/mac/linux machines in my house. i want this to be as "Hands-off" as possible when i get done setting it up. 

i also wanted to make a seperate partition on 1 drive and put the system on a 10GB partition, but i am having trouble getting a second partition on the existing drive to mount. i am getting an error message everytime i try to access that partition. i am not sure what mount point i should be setting this up as, or if that is the cause of the problem. if not i will just make another folder and share it from the same drive.

---

### Post by drudogg on 2009-11-08
maybe i put this in the wrong section? i got file and print working...

really need remote login, so i can access this from elsewhere, as well as remote control from computers in my house.

---

### Post by munchen800 on 2009-11-08
Just use ssh. You can stream media, access spreadsheets, whatever. If you need to administer with a gui use vnc. Use putty for ssh, and realvnc on your windows boxes to connect. If you are connecting via a Linux box you can bookmark the files on the server in nautilus with ssh://usename@your.wan.ip.here, then when you want to connect you click the bookmark and just enter the password. Make sure if you are behind a router forward port 22 for ssh and 5900 for vnc and USE A PASSWORD FOR VNC.

---

### Post by drudogg on 2009-11-08
thanks. i figured out how to make the thing connect, but now i ned to figure out how to make it start teh service on boot. i want this thing to be pretty headless. 

so how do i initiate a command on boot?

EDIT: i go t a command to run on boot...

but i lost all superkey functionality, and my menu is gone. so the vnc is working now, but the reason for it isn't. :(

so i can't execute anything, no terminal, no file manager... 

if anyone can help me i can boot in recovery mode and get cli, but not sure what to do.

i am running crunchbang 9.04 lite, and the command i added is to make the vnc program initialize on boot. i put it in the "run programs on boot" option.

---

