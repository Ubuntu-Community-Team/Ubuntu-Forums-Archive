---
title: "Bluetooth mouse persistent properties"
date: 2020-09-22
forum: Hardware
---

### Post by kino-lb1 on 2020-09-22
I'm using lubuntu:
Ubuntu 18.04.5 LTS
Codename:    bionic
----------------------------------
I recently purchased a bluetooth mouse and find it difficult to make speed and acceleration persistent.
I followed the advice given here:
----------------------------------------------------------------------------------
First install xinput
then
xinput --list --short
gives the connected device names.
This was:
BM30X mouse
On my Lenovo T440 laptop I used (in the terminal)
xinput --set-prop "BM30X mouse" "Coordinate Transformation Matrix" 0.5 0 0 0 0.5 0 0 0 1
to reduce the speed and acceleration by half.

This worked but did not persist on reboot so I had to include a script to run at startup.
------------------------------------------------------------------------------------
1. Create file under /home/username/.afterstart.sh

2. Write down commands to run on start.
sleep 10
xinput --set-prop "BM30X mouse" "Coordinate Transformation Matrix" 0.5 0 0 0 0.5 0 0 0 1
Note: had to add sleep or it didn't work.

3. Make sure script is executable.

4. Under path ~/.config/lxsession/Lubuntu/autostart you will find commands which run after the start.
Edit the file with command
sudo leafpad ~/.config/lxsession/Lubuntu/autostart

5. Add there /home/username/.afterstart.sh

6. Under Start > Preferences > Default application for LXSession you should now see the script

7. Reboot and see if it works.
-------------------------------------------------------------------------------------
That did work but now, if the laptop is inactive for a while and I have to login again the mouse speed and acc have reverted to original (high) values.
How do I make things persistent so that I don't have to run the script every time I log in?

---

### Post by kino-lb1 on 2020-09-23
OK so after more searching online I discovered the solution was to put the script in the ~/.bashrc file.

---

### Post by agvantibo on 2020-09-23
.bashrc is launched every time you open the shell. This is not what you would want, right? The best solution is the ubuntu settings app, here you can just change everything you need. [IMG]https://i.ibb.co/TqMfRVn/Screenshot-from-2020-09-23-12-32-03.png[/IMG]

---

### Post by kino-lb1 on 2020-09-24
That was the first thing I tried.
It doesn't work with a bluetooth mouse.

---

