---
title: "connection icon does not work"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by mike g on 2009-05-10
I just upgraded from 8.04 to 8.10.  I am able to connect to the internet but my connection icon says "no valid active connections found."

Does anyone have any idea to enable the connection icon?

I see several posts related to non connection but none dealing with just the non functioning icon.

Help appreciated,

---

### Post by pastalavista on 2009-05-10
I would first try restarting it. ```
killall nm-applet && nm-applet -sm-disable
``` and if that didn't fix it, I'd try to reinstall it ```
sudo aptitude remove network-manager-gnome -- purge && sudo aptitude install network-manager-gnome
``` and if that didn't work... well, I guess I'd come here and ask ;)

It would probably be best to run those commands separately, so just do the parts before and after the && as individual commands... I was in too big a hurry

---

### Post by mike g on 2009-05-10
ok, the first did not work so I removed and tried to reinstall the network manager but even though the network still works I no longer have the manager shown.

????????????????????

---

### Post by pastalavista on 2009-05-10
> **mike g said:**
> ok, the first did not work so I removed and tried to reinstall the network manager but even though the network still works I no longer have the manager shown.

????????????????????

What you probably did was remove the "Notification Area". Right-click the panel where it was and select "Add to Panel" then in the list of apps, select Notification Area. That's where the network manager runs... like the system tray in Windows.

---

### Post by mike g on 2009-05-10
Allow me to modify my last post.

I lost but was able to get back the "Network Configuration" short cut under System>Preferences.  It still shows no network connections, even though all networks function correctly.

I still am missing the Icon from the Panel even after adding the Notification area.

Basically confused and not quite sure why it happened with a simple upgrade.

Waiting to fix all the problems before I upgrade to 9.04

---

### Post by pastalavista on 2009-05-10
Ah, OK. That is just a launcher in the menu. It is the same as when you right-click the notification area icon and select "Edit Connections". My menu entry says "Network Connections". I don't understand why it would dissappear, probably because of the --purge part of the command but reinstalling it should have added it back. You can edit the menu and add it if you like. Do you know how to do that? 

edit: ps-- it is called "nm-connection-editor"

---

### Post by irv on 2009-05-10
Goto the Applications memu > Add and Remove Programs >System Tools >Network
Install it and it will be there.
If you have not tried wicd network manager yet I would recommend trying it. I use it and it works much better that the network manager that come with gnome. It is in the package manager.

---

### Post by mike g on 2009-05-10
Irv

I tried that and even though it says it was installed I still get no Icon in the Panel.  I actually tried it twice....

Something is not quite right here, I think.

---

### Post by pastalavista on 2009-05-10
To restart the network manager-- [alt-f2] nm-applet
to restart wicd (or start originally)-- [alt-f2] wicd

---

### Post by mike g on 2009-05-10
tried nm-applet and get a warning 
No Connections Defined"

---

### Post by pastalavista on 2009-05-10
I checked wicd in Synaptic and it said network-manager must be removed to install it. If you did what irv said, run wicd

---

### Post by mike g on 2009-05-10
Actually, this is for a wired connection.....

i really think there is something else amis because when I open my "Network Connections" which I now have back, it still shows no connections even though all networks are working.

This is all very strange, I am beginning to think I am missing something simple that is getting the "Network Connections" NOT to recognize what is working.  Still cant get the applet back.

---

### Post by irv on 2009-05-10
> **mike g said:**
> Actually, this is for a wired connection.....

i really think there is something else amis because when I open my "Network Connections" which I now have back, it still shows no connections even though all networks are working.

This is all very strange, I am beginning to think I am missing something simple that is getting the "Network Connections" NOT to recognize what is working.  Still cant get the applet back.

Go to this thread: [http://ubuntuforums.org/showthread.php?t=1146509&page=2]("http://ubuntuforums.org/showthread.php?t=1146509&page=2")
and do what the guy said in the second to last post and it should fix this problem. It worked for me.

---

### Post by mike g on 2009-05-10
I got this solved thanks to a friend of mine who, I did not know, was a Linux person. He said he had this same problem when he upgraded from 8.10 to 9.04.  It is his opinion that when the program upgrades it does not completely clean all the unnecessary items dealing with networking.

Ill do my best to explain.  

Do the following:  sudo gedit /etc/network/interfaces and then remove or comment out, it is your choice which, everything but --- 

                         auto lo
                         iface lo inet loopback

save and reboot.  

I got everything back as it was supposed to be including acknowledgment of what was connected in my wired network

Thank you all for your help!

---

### Post by mike g on 2009-07-09
I upgraded to J.J. and no longer have this problem.....but, as usual other problems have developed.

I love Ubuntu but it is NOT for the general non hands on computer user.

Thanks all for the help.

---

