---
title: "Missing HD space after deleting DVD::RIP!?"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by mcgarry83 on 2006-11-25
Im running Dapper. I just downloaded a program called DVD::rip. Its a good program, I liked it but I wanted to try something different, so I removed the program and deleted the .vob files that I ripped and the .avi files I made. Before I started I had 19gb of free space on my HD after all the ripping I did I had about 13gb left. After I removed the program and deleted all the files, I still had 13gb!? I emptied the trash, scanned the HD for the files or any similar files and found nothing. I have restarted the box and did everything I can think of. Has anyone else had this problem or have any suggestions on what to do to get back my missing 6gb?

---

### Post by eriefisher on 2006-11-25
I think dvdrip also creates working files that you have to tell it to delete when finished. If you didn't do this they might b building up. have a look.

---

### Post by jerrykenny on 2006-11-25
eriefishers right, look at the "hidden folders in your home directory . . . . . I think <ctrl> <h> for nautilus ?  probably its called /home/yourself/.dvdrip/

---

### Post by mcgarry83 on 2006-11-25
Ok, I deleted both of those files, there wasnt much in them anyway. Im still showing 13gb instead of the 19gb I should have. I have searched all the the files in the root directory. I have a 40gb hard drive. By my calculations, all my files add up to about 25gb. I know the OS takes up some but I know its not 15gb, there is some space that is unaccounted for. Anyone else have any idea? there was about 6gb of video files from DVD::rip, I have deleted them but didnt get the 6gb of space back.

---

### Post by mcgarry83 on 2006-11-26
Ok, I posted this in beginner talk but didnt get a good answer so I thought I would try here. This is my problem...

Im running Dapper. I just downloaded a program called DVD::rip. Its a good program, I liked it but I wanted to try something different, so I removed the program and deleted the .vob files that I ripped and the .avi files I made. Before I started I had 19gb of free space on my HD. After all the ripping I did I had about 13gb left. After I removed the program and deleted all the files, I still had 13gb!? I emptied the trash, scanned the HD for the files or any similar files and found nothing. I deleted the files in the home directory also. I have restarted the box and did everything I can think of. Has anyone else had this problem or have any suggestions on what to do to get back my missing 6gb?

---

### Post by taurus on 2006-11-26
Have you looked in /tmp?  Some programs like to use /tmp as a temp area where they dump some temp files...

---

### Post by Marsolin on 2006-11-26
Try emptying your Trash. Files stay in there after they are deleted and count against available disk space.

---

### Post by sam1 on 2006-11-28
i missing close to 30 GB in a 160 GB HDD.
NEEEEEEEEEEEEED HEEEEEEEEEEEEEEEEELP

---

### Post by mcgarry83 on 2008-01-24
solved. Found another trash folder in the root directory, that was hidden. The files were in there, deleted them and got my gb's back. Thanks for all the help.

---

