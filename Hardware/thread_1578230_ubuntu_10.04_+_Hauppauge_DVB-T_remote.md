---
title: "ubuntu 10.04 + Hauppauge DVB-T remote"
date: 2010-09-20
forum: Hardware
---

### Post by Janiporo on 2010-09-20
I am trying to set up XBMC (to standalone running on second desktop) , but this remote is killing me.

I have tried everything I can understand in this thread --> [http://ubuntuforums.org/showthread.php?t=1503385](http://ubuntuforums.org/showthread.php?t=1503385)
Especially in post 9. 
Step 5 in post 9 I can understand, step 6 Is beyond my capabilities. (and so is my english)

I_can_not_get Ubuntu to see my Hauppauge NOVA-T DVB-T (silver) remote controller as anything else, than keyboard. :confused:

I understand that Lucid does not handle this as older Ubuntus, this uses kernel module "ir-kbd-i2c" to do this. I have disabled and enabled that, I hawe installed the hauppauge remote fix, and everything else I have found that I can try.

With irw command in console I get only arrow and enter presses, as following:
```

irw
^[[D^[[A^[[C^[[B

^[[B^C

```

Output SHOULD be similar to this (with hauppauge 350-remote):
```

irw
0000000000001795 00 Down Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 01 Left Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001794 00 Up Hauppauge_350
00000000000017a5 00 OK Hauppauge_350
00000000000017a5 01 OK Hauppauge_350
```

Any help WOULD be appriciated...

:(

---

### Post by mycatsnameisbernie on 2010-09-20
It sounds like you have ir-kbd-i2c loaded, which treats the Hauppauge IR receiver as a keyboard. lirc is not used with ir-kbd-i2c. So it doesn't make any sense for you to be using irw.
 
MythTV has an "edit keys" feature, which allows the keycodes sent by ir-kbd-i2c to be mapped to your desired values. I don't know anything about XBMC, but it would need to have similar functionality in order for you to use ir-kbd-i2c.
 
In order to use the Hauppauge IR receiver with LIRC, you will need to figure out how to do all the steps of post #9, including step 6.
 
 

Other alternatives for you are:[LIST=1]
[*]Use Fedora instead of Ubuntu. Fedora comes with lirc_zilog built-in, so the steps in post #9 are not required, or
[*]Give up and buy an USB MCE remote, which will work with Ubuntu out-of-the-box.
[/LIST]> **Janiporo said:**
> I am trying to set up XBMC (to standalone running on second desktop) , but this remote is killing me.
 
I have tried everything I can understand in this thread --> [http://ubuntuforums.org/showthread.php?t=1503385](http://ubuntuforums.org/showthread.php?t=1503385)
Especially in post 9. 
Step 5 in post 9 I can understand, step 6 Is beyond my capabilities. (and so is my english)
 
I_can_not_get Ubuntu to see my Hauppauge NOVA-T DVB-T (silver) remote controller as anything else, than keyboard. :confused:
 
I understand that Lucid does not handle this as older Ubuntus, this uses kernel module "ir-kbd-i2c" to do this. I have disabled and enabled that, I hawe installed the hauppauge remote fix, and everything else I have found that I can try.
 
With irw command in console I get only arrow and enter presses, as following:
```

irw
^[[D^[[A^[[C^[[B
 
^[[B^C

```
 
Output SHOULD be similar to this (with hauppauge 350-remote):
```

irw
0000000000001795 00 Down Hauppauge_350
0000000000001795 00 Down Hauppauge_350
0000000000001796 00 Left Hauppauge_350
0000000000001796 01 Left Hauppauge_350
0000000000001797 00 Right Hauppauge_350
0000000000001794 00 Up Hauppauge_350
00000000000017a5 00 OK Hauppauge_350
00000000000017a5 01 OK Hauppauge_350
```
 
Any help WOULD be appriciated...
 
:(

---

### Post by Janiporo on 2010-09-21
If I disable this module with command: ```
sudo rmmod ir-kbd-i2c
``` nothing will change, ubuntu will still see this remote as keyboard...

I have No problem getting this to work with XBMC, IF I can get ubuntu to see this as remote, not keyboard. So this is NOT an XBMC issue.

Does Ubuntu see USB MCE remote as real remote, and does NOT interfere with other programs? (like opera, firefox, etc..)

Since I am trying to use XBMC dedicated on second desktop (with videoprojector), while using first desktop for netsurfing, photoshopping, or whatever. I do not want this remote no interfere with other programs.


Thaks for help =)

---

### Post by Janiporo on 2010-09-21
Do you think following will work?:
[http://www.dhgate.com/usb-pc-remote-control-18m-for-windows-2000/p-ff80808129b0c7be0129bb8e62a400dc.html](http://www.dhgate.com/usb-pc-remote-control-18m-for-windows-2000/p-ff80808129b0c7be0129bb8e62a400dc.html)

Because I dont..

Trying to find one.

---

### Post by Janiporo on 2010-09-22
Lets try with this one ;) --> [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230510383045](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=230510383045)

Just ordered it =)

---

### Post by shero77 on 2011-04-22
> **Janiporo said:**
> Do you think following will work?:
[http://www.dhgate.com/usb-pc-remote-control-18m-for-windows-2000/p-ff80808129b0c7be0129bb8e62a400dc.html](http://www.dhgate.com/usb-pc-remote-control-18m-for-windows-2000/p-ff80808129b0c7be0129bb8e62a400dc.html)

Because I dont..

Trying to find one.

you may have a try.:popcorn:

---

