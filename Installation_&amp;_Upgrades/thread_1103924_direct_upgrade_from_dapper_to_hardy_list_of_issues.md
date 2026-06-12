---
title: "direct upgrade from dapper to hardy: list of issues"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2009-03-23
Hello,

in this thread I would like to post my experience up to now on how the upgrade from dapper drake 6.06 to hardy heron 8.04 proceeded. I think that in the future I will edit this thread. So...

the installation went normally and in the end it asked me to reboot.

In the first reboot network wasn't working. In order to avoid that I restarted again and problem solved.

The icon of the manual configuration in the panel was blinking and as a result was very irksome. In order to avoid that I had to enable in visual effects the normal mode (via Change Desktop Backround after doing right click in Desktop).

Sound was not heard till the 5th reboot or so. The volume icon that appears in the panel appeared after the 3rd reboot or so. I tried to configure it clicking on many options, yet it refused to work. Kaffeine was complaining that output device is busy or something and rhythmbox exited with segmentation fault. After the 5th reboot a notification appeared that I had to type a command. Unfortunately I do not remember it yet in the end I put Live as an option and sound worked.

[COLOR="Magenta"]EDIT:[/COLOR]
Mounting devices and Connect to server via Places is not working till now.
[COLOR="#ff00ff"]mount is working by manually mounting at first and then by plugging a device and double clicking it via places [/COLOR]

Also the installation of deb files via double click is not working either. I had problems also with the Trash folder. No one was found. These issues are pending, so solution is still in question. 

[COLOR="Sienna"]EDIT1:[/COLOR]
Also opera refuses to work as it used to. Firefox on the other hand, up to now is working like a charm. 
[COLOR="#a0522d"]nope even firefox didn't start to work. I could ping via command line outside addresses, yet no browser opened any page. In order to fix that I did what I had done years ago:
[http://ubuntuforums.org/showthread.php?t=336073&highlight=telindus](http://ubuntuforums.org/showthread.php?t=336073&highlight=telindus)[/COLOR]

The optical effects are smooth and nice and I can connect via ssh (from terminal) as I used to. Wine is working out of the box and the lshw option is pretty updated (I still do not know whether the frequency of the memory card is diplayed though). Some options are refusing to open as for example the Software Sources and Add/Remove via Applications. aMSN worked also like a charm even though I had installed it via script. 

[COLOR="DarkOrange"]EDIT2:[/COLOR]
For skype downloading the static version at least it opens without any errors. Test is pending though.
[COLOR="#ff8c00"]test ok[/COLOR]

Graphic card is working as it used to, even though it does not enable me to change resolution. The dpgk-reconfigure command should be avoided. It messes things so moving the original file back to normal is required. 

The mount issue and the connect to server options are vital for me. I have searched the net, yet it not logical why these things are not working. My kernel is the latest one for Hardy, so these things are not so normal. At least this is what I think. 

That's all I can think of by now.

Till I edit this thread,
Regards!

---

### Post by mgmiller on 2009-04-30
> Connect to server via Places is not working till now.

Try this:
```
gksu gedit /etc/samba/smb.conf
```

scroll down a short distance till you find the line that says:
```
 ;  name resolve order = lmhosts host wins bcast
```

change it to this:
 ```
  name resolve order = lmhosts wins bcast host
```

Notice I have removed the ";" from the front of the line and changed the order of the listed items.

Click save and you may have to log off and back on, or at worst, restart.  The network browsing should return to normal.

---

### Post by Claus7 on 2009-05-01
Hello,

thanks for your response. I just created this thread, so if someone follows the same steps as I did, to be able to solve some problems. I do not use this partition with hardy at the moment and I'm considering at putting it to rest (the hdd is old enough).

Good to have a solution. Yet, I think that I had tried it before without any result. I think that the upgrade I made was not the most successful one could do.

Regards!

---

