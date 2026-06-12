---
title: "I Am not able to download any pakages.. from ubuntu's repository.."
date: 2008-10-20
forum: General Help
---

### Post by aprashanth on 2008-10-20
I Am not able to download any pakages.. from ubuntu's repository..
Please help me..
i am struggling from past two weeks to rectify this problem..

---

### Post by jerome1232 on 2008-10-20
What are the errors if you try it from the commandline? (i'm just using jfsutils in my example you can try to install whatever)

```
sudo apt-get update
sudo apt-get install jfsutils
```

---

### Post by aprashanth on 2008-10-20
> **jerome1232 said:**
> What are the errors if you try it from the commandline? (i'm just using jfsutils in my example you can try to install whatever)

```
sudo apt-get update
sudo apt-get install jfsutils
```


This is the error that i am getting..


Err [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                                                  
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://ftp.wcss.pl](http://ftp.wcss.pl) hardy Release.gpg                                                            
  Could not connect to ftp.wcss.pl:80 (156.17.193.34). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN                                    
  Could not connect to archive.canonical.com:80 (91.189.90.142). - connect (111 Connection refused)
Err [http://ftp.wcss.pl](http://ftp.wcss.pl) hardy/main Translation-en_IN                                                 
  Could not connect to ftp.wcss.pl:80 (156.17.193.34). - connect (111 Connection refused)
Err [http://ftp.wcss.pl](http://ftp.wcss.pl) hardy/restricted Translation-en_IN
  Could not connect to ftp.wcss.pl:80 (156.17.193.34). - connect (111 Connection refused)
0% [Connecting to ftp.wcss.pl (156.17.193.34)]

please help..

---

### Post by jerome1232 on 2008-10-20
Try changing your server.

System-Administration-Software Sources. Select 'other' from the dropdown menu next to 'Download From'

Hit the button that says 'Select Best Server' have a soda while you wait for it to ping a million servers then try to do the update command again.

---

### Post by aprashanth on 2008-10-20
> **jerome1232 said:**
> Try changing your server.

System-Administration-Software Sources. Select 'other' from the dropdown menu next to 'Download From'

Hit the button that says 'Select Best Server' have a soda while you wait for it to ping a million servers then try to do the update command again.

i am from India.. when i gave the Select best server..
after few test it gave error saying that no No suitable download server was found

can i opt for a different country?...

---

### Post by jerome1232 on 2008-10-20
Yeah try some other countries. Are you able to get internet from that Ubuntu install?

---

### Post by rakris on 2008-10-20
change in /etc/apt/sources.list to "in.archive.ubuntu".. 

Something like that. Prefix "in" insstead of "my" in URL.

Are u sure you are not connected to internet through proxy????

---

### Post by aprashanth on 2008-10-20
> **jerome1232 said:**
> Yeah try some other countries. Are you able to get internet from that Ubuntu install?

thank you..
it worked.. thanks a lot..

---

### Post by aprashanth on 2008-10-20
> **rakris said:**
> change in /etc/apt/sources.list to "in.archive.ubuntu".. 

Something like that. Prefix "in" insstead of "my" in URL.

Are u sure you are not connected to internet through proxy????

.............................................................
it worked by choosing the server from software sources..
anyways thank you for  to helping me..

---

### Post by rakris on 2008-10-20
You actually must have done the same thing in UI :)

congrats..

---

### Post by jerome1232 on 2008-10-20
Yeah that's what the software sources gui does :p Pings servers in the country (changable) and automatically adjusts sources.list to point to the fastest server it could find.

Glad we could help and don't forget to mark your thread as solved so that others know there's a solution to the problem in this thread.  (Upper right, thread tools)

---

### Post by aprashanth on 2009-10-16
Thank you.. to all.. 
I was able to fix it.,

---

