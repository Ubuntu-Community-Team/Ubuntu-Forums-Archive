---
title: "How do I send files directly to my friend on WIndows?"
date: 2008-08-10
forum: General Help
---

### Post by boom2k1 on 2008-08-10
I have to send her some large files.
Sending it through MSN is super slow, as everyone knows.
I could send it through Skype, except she wouldn't want to install Skype.

I don't want to upload it anywhere for her to download. I just want a simple direct file transfer program (and I don't have to register anything) that works very well and is not called Skype.

What are my options?

Thanks

---

### Post by lisati on 2008-08-10
Does Yahoo have a similar option?

---

### Post by y@w on 2008-08-10
You could always setup an apache or ftp server on your end. It'll mean a little bit of footwork for you, but she won't have to do anything except for click on a link. You can also use WinSCP if you have SSH open on your machine.

---

### Post by boom2k1 on 2008-08-10
No.. that's the thing.. I want no part in ssh, don't like setting up a server, and I thought Pidgin doesn't have file transfer implemented in Yahoo messenger.

I don't like doing things the geeky way, nor would my friends want. Having her to look up her own IP would be her limit.

Any other ideas?




Thanks

---

### Post by jerome1232 on 2008-08-10
If you installed apache and just slapped a simple html file with a link to the file, and the file into apaches folder, all she would have to do is type your ip in a browser and click the link. Nothing hard about that.

I thought it was a good idea :)

---

### Post by y@w on 2008-08-10
Yeah.. Not a ton you can do without using a new IM client, setting up some sort of server, or uploading it to a transfer service.. I've transferred files using netcat to open up a socket to dump a file to the network and connecting from the remote end. It's fast, but I'm guessing out of the question in this situation. Of course you could always mail her a CD or flash drive :)

---

### Post by pastalavista on 2008-08-10
I know I'm kinda old-school, but I've always depended on IRC. She couldn't download Pidgin?.. there is a [Windows version]("http://www.pidgin.im/download/windows/").

---

### Post by DGortze380 on 2008-08-10
Ok, so no IM that will work, no e-mail, no server...

burn a disc and mail it?

---

### Post by boom2k1 on 2008-08-10
Actually, cool! I never knew IRC could do the job.

How does IRC sending files work? Does it pass through the server I connect to?

---

### Post by pastalavista on 2008-08-10
[Wikipedia explains]("http://en.wikipedia.org/wiki/Internet_Relay_Chat") it better... too much to type haha..be careful, IRC is no way secure.. zip the file and/or encrypt it if it's secret ;)

---

### Post by y@w on 2008-08-10
haha I say just use floppy disks :)

---

### Post by sujoy on 2008-08-11
ftp ftw!!

install vsftpd, edit /etc/vsftpd.conf and enable local users. thats it. now your friend  can literally browse your HDD via ftp and download anything.

Just give him this link
[ftp://username : password@yourIP](ftp://username : password@yourIP)

---

### Post by cariboo on 2008-08-11
BUy a usb thumb drive, copy the files to it and give it to her. Sneakernet rules :)

Jim

---

