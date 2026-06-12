---
title: "How to format a USB stick for file backup"
date: 2013-04-07
forum: Hardware
---

### Post by breezypt on 2013-04-07
Every timeI format my USB stick to ext4, it formats fine, but I can't copy over any files to save. I look under permissions and it says I am not the owner, root is the owner. I didn't format the drive signed in as root, I formatted it signed in as administrator under my user name.
 I just want to be able to back up important docs, like reciepts and long passwords onto a USB stick.

I'm on ubuntu 12.04 that is on an ext4 partition & that is how I formatted the USB drive. I'm already signed in how can I NOT have permsissions? I don't understand why this is so hard.

I would love to password protect this USB drive... pop it in and save a file directly to it, but I'll settle for just being able to copy a file over...

Can someone help me? AM I using the wrong app (gparted), perhaps there is a utility app similar to Mac OS where you could do all of this from?

Thanks for any suggestions or help.

---

### Post by ibjsb4 on 2013-04-07
In terminal

```
gksudo nautilus
```

On the left side you should see your stick.  Right click on it and go to properties>permissions and change the owner.

---

### Post by breezypt on 2013-04-07
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1729120_14.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1729120") 				 				 					 						 	[**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120"), Thanks for the response.

For anyone who has had this problem. Nautilus was already installed. So I did some digging, and found 'Disk Utility' it is very similar to OSX's for anyone familiar with that OS. I was able to reformat the USB disk to msdos, then make a Fat partition and put a password to it. So now when I put in the drive it askes for a password and allows me to copy and remove files. I used this format because it says it is the best solution to be read from just about any OS. With an 8 gb USB drive, it will hold a ton of text files before getting full. I just need it for the important ones. My firewall I used a 64 character password that I can not remember, so I put in in a text file, and when I need to get into my firewall I just copy and paste the password from the text file. Now if I can figure out how to encrypt a file in Ubunto I'll be set. Anyone know the commands for that in the CLI?

---

### Post by pdc on 2013-04-08
[http://lmgtfy.com/?q=how+to+encrypt+a+file+in+Ubuntu#](http://lmgtfy.com/?q=how+to+encrypt+a+file+in+Ubuntu#)         

:)        :)

---

### Post by oldfred on 2013-04-08
Someone just asked in another thread.

bcrypt was the answer, when I looked at it in synpatic there were a lot of encryption tools.
ccrypt was another tool in synapatic.

---

