---
title: "mount of shares not working with Intrepid &amp; wireless network."
date: 2008-11-11
forum: General Help
---

### Post by HereInOz on 2008-11-11
Hi All,

For some while now, through both gutsy and hardy, I have been mounting a samba share on startup with an entry in fstab.  

I use a wireless connection and the mount would always take place after the wireless network connection had provided the connectivity to the server where the samba share resides.

Now that I have upgraded to Intrepid, the mounting of the samba share does not happen, until I do "sudo mount -a" in a terminal.  However if I use a wired network connection, the mount happens OK, just not with the wireless.

Seems that I need a way to have fstab try again once the wireless network is up and running, but I don't know if this is possible.  Can anyone assist with this?

---

### Post by Gjallarbru on 2008-11-26
Hi, I just have a bit more experience than a noob, but I have 2 ideas.

1) Check to see if you don't have a "noauto" option in your fstab entry.

2) In system>preferences>sessions add an entry with the command "mount -a"... name it remount or something.  (I'm translation from my french menus mind you)

I'm not saying this is the best ideas possible, I'm just above a noob, so what do I know?

Hope this helps.

---

### Post by doas777 on 2008-11-26
my first guess is that the mount is attempted before the wifi connects. 
HereInOz's suggestion about mounting after login with the sessions manager is a good bet.

good luck

---

### Post by Gjallarbru on 2008-11-26
Doas777 reminded me something...

If the solutions I gave you don't work, the solution must be in the /etc/rc#.d directories. (replace # with a number from 0 through 6)

The network process must have a higher process than that of the nfs mounting (so one happens before the other).  Problem is, I don't know which directory it is, nor what process to look for, but you might want to google this path.

Once the process are identified you can move priority around with a command like: 

ls -la /etc/rc6.d (to see current order)

sudo mv S31someprocess S14someprocess (to change priorities).

If you figure this idea out, it would be an actual fix... my other solutions are simple but only hide the problem.

---

