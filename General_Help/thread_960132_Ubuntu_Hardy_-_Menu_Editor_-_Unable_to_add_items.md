---
title: "Ubuntu Hardy - Menu Editor - Unable to add items"
date: 2008-10-27
forum: General Help
---

### Post by barlaventoexpert on 2008-10-27
I have spent quite a bit of time researching this on google and in these forums and am stumped.

I run Hardy on a Acer 4310 laptop. There is a root user and my own login user as I am the only user.

I wish to add items such as font viewer to the "other" section of the application menu on my user name.

When I open Menu Editor and navigate to the relevant section to tick the necessary box the item e.g. "font viewer" is in italics and cannot be enabled.

I have follow advice and rebooted the machine navigated to the recovery console and run "usermod -a -G admin" - no success.
 would
when I run id in console:

I get: 

uid=0(root) gid=0(root) groups=0(root)

Any ideas how to resolve this would be appreciated.

---

### Post by ajgreeny on 2008-10-27
Do you mean you have set up a root account, which is normally not the way Ubuntu is used?  Anyway, aside from that, try adding a new item to the section you want and then use the command **gnome-font-viewer %u** in the command box.  I assume you have **gnome-font-viewer** installed.

---

### Post by barlaventoexpert on 2008-10-27
> **ajgreeny said:**
> Do you mean you have set up a root account, which is normally not the way Ubuntu is used?  Anyway, aside from that, try adding a new item to the section you want and then use the command **gnome-font-viewer %u** in the command box.  I assume you have **gnome-font-viewer** installed.


Thanks for the reply.

No, I do not want to set up a root account.

I have my main account to which as far as I can ascertain has been granted full admin rights.

The problem is that in the various sections of Menu Editor there are items that are in italics and will not allow me to enable them. (i.e. check the tick box.)

Thanks for you suggestion - I tried it and got the following message:

"Could not save launcher

Failed to create file '/home/cgkh/.local/share/applications/alacarte-made.desktop.OMOVJU': Permission denied" 

It appears that certain folder permissions are incorrect.

Any ideas would be very helpful.

---

### Post by drs305 on 2008-10-27
You can change the ownership of that specific folder with:
```
sudo chown -R cgkh /home/cgkh/.local/share/applications
chmod -R 750 /home/cgkh/.local/share/applications 

```
This assumes "cgkh" is your username.

---

### Post by barlaventoexpert on 2008-10-27
> **drs305 said:**
> You can change the ownership of that specific folder with:
```
sudo chown -R cgkh /home/cgkh/.local/share/applications
chmod -R 750 /home/cgkh/.local/share/applications 

```
This assumes "cgkh" is your username.

Thanks so much! That did it!

I had already figured that it was a permissions problem after the last post but had not yet got round to looking at it as busy on other things.

I need to track down also why it happened.

Many thanks to all again.

---

