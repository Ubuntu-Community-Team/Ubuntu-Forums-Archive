---
title: "&quot;No root file system is defined. Please correct this from the partitioning menu.&quot;"
date: 2008-09-17
forum: General Help
---

### Post by pawanspace on 2008-09-17
I have installed ubuntu using Wubi 8.04.1 windows installer as dual boot with windows by following the same method given in installation guide. 
Installation was successful but when I tried booting ubuntu I got folowing error :

[COLOR="Red"]**"No root file system is defined. Please correct this from the partitioning menu." ** [/COLOR]
:(:(
Please let me know what can be done for this. I am really looking forward to use Ubuntu. I hope to get a posiive and fast response from your guys. Thanks!

Regards,
Pawan Chopra.

---

### Post by Partyboi2 on 2008-09-17
try uninstalling wubi then running
```
chkdsk /r
``` from a command prompt, then reinstalling.

---

### Post by pawanspace on 2008-09-17
Have tried your solution but still I am facing same problem.
Please help. thanks.

---

### Post by pawanspace on 2008-09-17
Is there anyone who can help me on this?
please let me know. I have to solve it urgently. Thanks in advance!

---

### Post by Nuuk on 2008-09-18
Please see this post

 [http://ubuntuforums.org/showpost.php?p=5731340&postcount=7]("http://ubuntuforums.org/showpost.php?p=5731340&postcount=7")

---

### Post by Partyboi2 on 2008-09-18
> **Nuuk said:**
> Please see this post

 [http://ubuntuforums.org/showpost.php?p=5731340&postcount=7](http://ubuntuforums.org/showpost.php?p=5731340&postcount=7)
His/her problem seems to be that they are receiving that message after they have installed ubuntu with wubi, the link you provided is good if one wanted to install ubuntu to its own partition. :)

---

### Post by dmizer on 2008-09-18
Moved to the wubi section of the forum. You're more likely to get help specific to your problem this way.

---

### Post by ago on 2008-09-18
uninstall and reinstall
boot in verbose mode (press esc at boot and select the verbose option) 
if that happens, press ctrl+alt+f2
run /custom-installation/hooks/failure-command.sh

there should be a file in windows: C:\ubuntu\installation-logs.zip
attach it here

---

### Post by pawanspace on 2008-09-18
I tried running your command
I got following error:

[B][COLOR="Red"][104.596809] b43-phgo Error: firmware file 4b43/0code5fw" not found or load failed

[104.596809] b43-phgo Error: you  must go to [http://linuxwireless.org/en/users/drivers/b43#](http://linuxwireless.org/en/users/drivers/b43#) devicefirm ware and download the current firmware(version 4)

[105.615421] b43-phgo Error: firmware file "b43(ucode5.fw)" not found or load failed.[/COLOR][/B]

Please let me know what can I do? 

Thanks in advance,
I am really happy that I am getting  feedback from you guys.

Pawan

---

### Post by ago on 2008-09-18
The wireless firmware should be irrelevant.

You can also see the log from console (ctrl+alt+f2) using the command

less /var/log/syslog

---

### Post by pawanspace on 2008-09-29
Hi, 


I am unable to run any of given command plz help me I am unable to solve this problem. Its already 15th day of my problem. Please help me to solve this. Thanks. 


Pawan

---

### Post by ago on 2008-09-29
as mentioned above you have to press ctrl+alt+f2 to get a terminal so that you can type commands in.

---

### Post by pawanspace on 2008-09-29
I tried this thing as mentioned above but I am getting following error:
[COLOR="Red"]
[104.596809] b43-phgo Error: firmware file 4b43/0code5fw" not found or load failed

[104.596809] b43-phgo Error: you must go to [http://linuxwireless.org/en/users/drivers/b43#](http://linuxwireless.org/en/users/drivers/b43#) devicefirm ware and download the current firmware(version 4)

[105.615421] b43-phgo Error: firmware file "b43(ucode5.fw)" not found or load failed.[/COLOR]

---

### Post by ago on 2008-09-29
ctrl+alt+f3

---

### Post by pawanspace on 2008-09-29
I have attached [COLOR="red"]installation-logs.zip[/COLOR] with it ,I have installed ubuntu on a different partition.  

One more thing I get warning when ubuntu starts booting:

[COLOR="Red"]Warning: unrecognized partition table for drive 80. Please rebuild it using Microsoft-compatible FDISKTool(err 3)
C/H/S=16383/255/63[/COLOR]

I think we are colse to the solution and we will solve it very soon. Thanks!

Pawan Chopra.

---

### Post by ago on 2008-09-29
Could you do an installation in verbose mode (press esc at boot) and post the logs again?
Also please post the output of 

cat /proc/partiotions
cat /proc/mounts

---

### Post by vravit on 2011-03-12
May I know the laptop model?
When Pressing ctrl+alt+F2 if its a dell model then you need to press ctrl+alt+fun+f2.

since pressing only f2 is for activating wireless module.
and fun+f2 = f2.


Hope this helps even though its a little late...

---

