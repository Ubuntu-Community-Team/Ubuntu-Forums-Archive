---
title: "sharing /var/www via samba on intrepid"
date: 2008-10-31
forum: General Help
---

### Post by garethsimpsonuk on 2008-10-31
Hello ppl,

Well it's been a few months since I used ubuntu as I've been away working. I need to setup a LAMP testserver so i can test php scipts locally before running on live webservers. 
I've been waiting for intrepid to come out before I install and 

I'm just going through the process now. Here's what I've done so far:-
- Installed I-Ibex server
- Installed Samba and LAMP server automatically using installer
- Installed webmin
- Installed phpmyadmin

and that's it. I've tried to share /var/www through webmin. it shows up in network but the directory isn't modifiable through windows. i guess it's a permission issue ( oh the memories! ). 

Could someone please let me know how i can do this. I'm a bit rusty with linux at the moment so I just want a quick and dirty samba config file that shares /var/www with full permission for everything. it's only a test server and it's always behind a firewall so I'm not too bothered about security.

Any help would be greatly appreciated guys,

It's good to be back on Ubuntu! I missed it.

Thanks

---

### Post by Johnsie on 2008-10-31
sudo chmod -r 777 /var/www

makes anyone able to do anything with the files. However that is not the most secure way. I would probably change the owner of the folder instead so that the folder is owned by the same user that samba is set to be in /etc/samba/smb.conf

I think 'chown' is the command you need to find out about for changing owners of files and folders but I'm not sure.

---

### Post by Johnsie on 2008-10-31
actually the more I thik about it the more I think 777 is a bad idea. Change the owneship of the files because giving  www 777 chmod permissions  is bad security practice.

---

### Post by garethsimpsonuk on 2008-10-31
I tried a chmod and it locked me out, i got the syntax wrong. it wouldnt let me put the 777 in anywhere so i entered it without it and it's done something. 

i've tried chown gareth /var/www but it's still locked can you give me the command to reverse my permission changes pleaase?

i tried chmod /var/www.

thanks for the reply

---

### Post by Johnsie on 2008-10-31
mmm i prolly gave you the command badly sorry:

sudo chmod 777 /foldername

 still wouldnt recommend it though

---

### Post by garethsimpsonuk on 2008-10-31
yea that's worked, thanks.

it probably couldn't be anymore insecure. the samba config is a quick guest setup and /var/www is at 777. i assume it should be ok on my home network but i do have ports open to another server on my router.

should be ok for now tho. i just don't want to go through the nightmare i've had in the past with samba.

cheers for the help

edit: only problem is that 'testserver' is showing up twice in my network. a reboot hasn't fixed it

---

