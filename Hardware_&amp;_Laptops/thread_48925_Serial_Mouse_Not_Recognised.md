---
title: "Serial Mouse Not Recognised"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by jayani on 2005-07-14
For the first time in my life i have installed Linux OS. i.e., Ubuntu. But the serial mouse on my system is not recognised. its working fine in if a boot through win98. Please help me.
Thanks

---

### Post by Teroedni on 2005-07-14
[http://www.ubuntuforums.org/showthread.php?t=45443&highlight=serial+mouse](http://www.ubuntuforums.org/showthread.php?t=45443&highlight=serial+mouse)
Might be a solution

if this is too advanec tell me and i would try to help you here

---

### Post by jayani on 2005-07-14
I have seen that link. But i am not so techie to understand this. What shall i do?. My system is Celeron based with Mercury Mobo.
Thanks

---

### Post by Teroedni on 2005-07-14
okey i need to see your xorg.conf file

Open Terminal
right click>open terminal

copy this and paste in terminal:

sudo gedit /etc/X11/xorg.conf



Copy all text and paste here

---

### Post by Teroedni on 2005-07-14
Can you tell me which mouse it is 
Microsoft 
Others?

---

### Post by jayani on 2005-07-15
Its other general mouse and is recognised in windows as standard mouse. As the mouse is not at all working, i hv gone through the release  notes of Genome Desktop and used the Keyboard shortcuts.

with Alt+F1- i hv opened the application menu and selected Run application.
In this i typed Sudo gedit /etc/x11/xorg.conf. Selected Run in termianal and made it to run.

The Terminal is opened and it has asked the password. After i entered the password, it has given the following message

(gedit:6340): Gdk-warning**:locale not supported by lib
(gedit:6340):Gdk-warning**:can not set locale modifiers

After this it is opening a new terminal with filename xorg.conf. There are no commands in this.

I have closed it and back to normal.

There is no ps/2 provision for this system and hence i was unable to test with  connect another mouse. Any how the system is working fine with Keyboard. 

And when i have installed the same OS in another system with PS/2 mouse the mouse is also working fine there.

If you can suggest me some way to proceed i will do it.

Thanks

---

### Post by Teroedni on 2005-07-15
Your problem with the mouse is that it loads the wrong driver, so i think we can fix this. We just have to choose the right driver from the devices folder:)






Since gedit dont work :-# 
try

sudo nano /etc/X11/xorg.conf


If nano doesnt work either >
We may have an faulty installation. [-X 
So if nano not works 
Reinstall Ubuntu

By the way: You know you have to type sudo in lowercase?
Just wonder since you posted sudo with a big S here
Also
not
Sudo nano /etc.....
but the right one
sudo nano /etc......

---

### Post by jayani on 2005-07-16
Thanks for the response. I have tried the other option also but it is also not useful. (of course i was using 's' as mentioned by you). After this i have formatted the whole system (including Windows Partition) and installed ubuntu. But the same problem continues. Can you suggest any more?

Thanks
Jayani

---

### Post by wvslkr on 2005-07-16
Try this: [https://wiki.ubuntu.com//SerialMouseHowto](https://wiki.ubuntu.com//SerialMouseHowto) :)

---

### Post by Teroedni on 2005-07-17
Does it works now?

---

### Post by jayani on 2005-07-18
I followed the procedure.  But the problem is not solved. Though i am selecting the mouse port as //dev/ttys0, it is staying in default i.e., //dev/input/mice.

If i open it again it is set in //dev/input/mice only. Is there any specific procedure to chhose the port and save the settings?

Thanks

---

### Post by Teroedni on 2005-07-18
The most important first
Can you use Nano to edit. I hope you can because we have to edit xorg.conf .Is the xorg who decides what driver who is gonna load. It worked last time i shut myself out.

I am sorry but i cant help before we  have fixed that.

---

### Post by jayani on 2005-07-18
:smile: Hay! I hv got it. Thanks a lot for your help! I do not know how its working but its working fine. Morning as i told i hv tried it and was not working. I swithed off the sytem and now when i swithched it on, the mouse is working.

Thanks again

---

### Post by Teroedni on 2005-07-18
Great  :-P

---

