---
title: "Help with NFS!!!"
date: 2005-11-23
forum: General Help
---

### Post by Eleaf on 2005-11-23
Please!!!!  I need help!  I've been trying to get this to work for days!  I cannot understand why it won't work!!!

I have done everything I can to set up this computer to serve a nfs folder so the other computers can access it.  I'm trying to set up a render farm.  I have followed all the instructions for setting up nfs from the wiki.  So far, the only thing I can do is access the nfs folder from the computer hosting it!  It mounts fine if I do 'sudo mount localhost:/mnt/shared /mnt/test' (or wherever I want to mount it)  However, I can not get this to work on any other computer.  I put in 'sudo mount 192.168.1.101:/mnt/shared /mnt/test' and it just says after a while that it times out.  I've messed with all the exports and every file having to deal with nfs.  But I can't get this to work!

Can you not mount nfs using the ip address?  Does it have to be a domain name?

---

### Post by kevcool on 2005-11-23
Maybe you've seen this thread but in case you haven't:

[https://www.ubuntulinux.org/support/documentation/faq/nfs-server](https://www.ubuntulinux.org/support/documentation/faq/nfs-server)

It's likely that you need to change portmapper if you've not done that.  The fact that you're using the IP address should be inconsequential.

---

### Post by Eleaf on 2005-11-23
Yes, I got rid of the portmapper thingy.

But everything is still the same.  When I try and mount the NFS folder from the other computer, it just says "mount: RPC: Remote system error - Connection refused"

This is insane...  Help!!

---

### Post by Eleaf on 2005-11-23
Ok, it suddenly started working...  I don't think I would ever be able to successfully setup up another nfs folder.  That was so much work and I don't even remember all the things I had to do.... X.X  I also don't know why it just randomly started working.  I'll need more help later probably...

---

### Post by Eleaf on 2005-11-23
Alright, now I want the other computer to be able to change and execute files.  However, whenever I try and do this, it just says "cannot execute binary file" or "Permission Denied".  
How do I allow higher access to these files?  If I do sudo on that side, it doesn't change anything.  So I think I need to change something in the /etc/exports options for that directory.

---

### Post by Eleaf on 2005-11-23
I seriously need help to allow full permissions to others accessing the nfs folder.  This is important!  It is only allowing read access.  How do I change this?

---

### Post by fimbulvetr on 2005-11-23
Please paste your /etc/exports file.

Also, this has nothing to do with this problem, but remember that all clients that are to access the nfs server need portmap installed.

---

### Post by Eleaf on 2005-11-23
Ok, This is my /etc/exports file.
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).

/mnt/shared     192.168.1.0/255.255.255.0(rw,no_root_squash,sync) 

```

I think they all have portmap installed as well.  I have nfs working for the clients, I can read all the files etc, but I can't execute or edit anything.  Which I need to do...  = P

Thanks!  .

---

### Post by tabinin on 2005-11-23
Your permission problems probably have more to do with the permissions for the file/folder on the server side more than with NFS itself.  Check to make sure that the file or program that you want to execute is either 1) set to allow "others"rights or 2) owner and group have rights **if** the user/group IDs are the same and set up on both the server and the client.  (The former is the less secure of the two.)  

For my server, I make the owner/group ID (numbers, not just names) match between machines.  So, files on the server are owned by user ID XYZ and my user account on my desktop (client) is also user ID XYZ.

See if that works for you.

---

### Post by Eleaf on 2005-11-23
Ok, well how do I set the permissions for it to a user id?  It is set to root right now and I don't know how to change its permissions to another user id.  The user id's on both machines have the same name and the same id.

---

### Post by tabinin on 2005-11-24
Since you have the same users/IDs on both machiines, you only need to change ownership of the files/binaries to the user you will be using on the client machine (other forum members may have a better solution, but this one is one that should work).

See the man page for chown.  Generally, it goes like this:

```
sudo chown user:group file
```

or to make it apply to a folder and all files and folders below that (recursivley)

```
sudo chown -R user:group file
```

---

### Post by arphe_el on 2005-11-25
i try to edit the /proc filesystems to insert some lines "insmod nfs" to work but i can't edit the file i use the sudo gedit /proc filesystems but as i save it 

Could not save the file "/proc/filesystems" prompts me

is there any command to override the file?

i check the portmap, rpc.statd, rpc.lockd all of them are running fine 

but when i try to mount the share folder in my case i use the ip address as server looks like this command to terminal

# sudo mount 192.168.1.101:home /mnt/home

i get this message error! "home failed, reason given by server: Permission denied
"

please note that i run the portmap, rpc.statd and rpc.lockd on both server and client.

any suggestions? 

thank you and GODspeed!

---

### Post by greenway on 2005-11-26
@arphe_el

First, I would check you etc/hosts.deny file. I had the same problem before and solved it (kind of) by making sure this file is empty. As long as you configure your /etc/hosts.allow file correctly, you should be ok security wise.

The other part of my problem was the fact iptables was blocking the mount requests from the client. So checking you firewall might also be a good idea. Still working on this issue; using portmapper is a pain in the bud! It's keeps switching the mount to a different port. Anybody any suggestions on how to bypass portmapper and mount on the same port all the time. I know I can punt the option "port=****" in fstab although this doesn't really seems to work. Any suggestions anyone??

---

