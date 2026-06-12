---
title: "file sharing with Windows Vista"
date: 2008-09-27
forum: General Help
---

### Post by 2panther on 2008-09-27
Hello!

I installed Ubuntu Desktop last night on an older machine I had laying around and the install went off without a hitch. I want to use this box as a file share for my main machine which is running Windows Vista Ultimate x64.

I thought I had everything setup properly but I'm having some issues. I'll do my best to explain them as I'm new to linux.

I created a folder called "share" and I added some mp3's and some dvd rips to the ubuntu box via a usb thumb drive. I right clicked the folder and went into sharing and checked all three boxes, clicked modify permissions. When trying to access them from my vista machine I can get into the folder but when trying to listen to the song or movie I get an access is denied error.

If I add files to the ubuntu box from my vista machine I have no issues viewing or modifying them but when I look at the files I added from vista on the actual ubuntu box they have a little lock icon on them and I can't move, copy or delete them on the ubuntu machine. 

I'm guessing I'm missing something small here but it's driving me mad because it's not working the way I'd like it to. 

What can I check to see that I've got everything setup correctly? Please remember I'm new to linux so go easy on me!

Please let me know what other info I can provide to help troubleshoot this issue.

the path on the ubuntu box is home/carter/share/

---

### Post by kokkus on 2008-09-27
To access the locked files which is locked for security reasons, open nautilus with gksudo command (gksudo nautilus) in terminal.
Go to properties on all the locked files, go to promissions and add all of them to read / write and delete / modify.
Read / write has not been set to the files since you can't access them from windows. So mark all files in your share folder and do the same process.

---

### Post by 2panther on 2008-09-27
i ran the command you suggested and this was the result

"Initializing nautilus-share extension

** (nautilus:6148): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS"


it then opened a file browser titled root and within that window I'm unable to navigate anywhere.   :confused:

---

### Post by cariboo on 2008-09-27
What if you click on File System in the side panel? If you don't have a side panel go to View-->Side Panel.

Jim

---

### Post by kokkus on 2008-09-27
You do not have root promission if you do that. That's why u have to run nautilus root command.

---

### Post by 2panther on 2008-09-27
while in the root - File Browser I can only navigate to the desktop, anywhere else takes me out of the root window.

---

