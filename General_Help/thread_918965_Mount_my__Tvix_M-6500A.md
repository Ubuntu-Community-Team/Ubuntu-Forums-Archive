---
title: "Mount my  Tvix M-6500A"
date: 2008-09-13
forum: General Help
---

### Post by blobban on 2008-09-13
Hi 

Im all new to Ubuntu so I dont know much about linux. 

The thing is I have a  Tvix M-6500A andI want to be able to see it in Ubuntu

Does anyone know how to do?

thx in advanced

---

### Post by snijper on 2009-01-05
Hi blobban,

Here is the tutorial , I have just found it on internet, you can just follow,

with my ubuntu 8.10 64 bit and tvix M-6500A, it worked perfect.

Good luck...

Setting up a NFS (Network File System) protocol in Debian is quite easy.  Essentially there is two ways of implementing NFS; a software way that runs in user-land memory, and a kernel way that runs in kernel-land memory.  I personally believe the kernel approach is more stable and fast, so it is what I discuss below.
First use apt-get and install portmap; which is our daemon that will dictate what computers to allow/deny privelages to.  And also install nfs-kernel-server.... The NFS daemon server that runs in kernel-land.

$ sudo apt-get install portmap nfs-kernel-server

In my particular home setup, I use gateway 192.168.1.1 off the router, so in the file hosts.allow I give all privelages to my machines.  You can leave the last address field of each entry blank if you want this to behave like a wildcard.

$ cat /etc/hosts.allow
mountd: 192.168.1.
statd: 192.168.1.
portmap: 192.168.1.
rquotad: 192.168.1.

It is also important to deny everyone else (those machines that aren't in my network).  The file hosts.deny will actually be processed first, and then hosts.allow will be processed (by portmap).

$ cat /etc/hosts.deny
mountd: ALL
statd: ALL
portmap: ALL
rquotad: ALL

The file /ext/exports explicitly states what directories we want to share on the system that is the acting as the NFS server.

$ cat /etc/exports
/tvixhd1  192.168.*(rw,sync,no_root_squash,no_subtree_check)

In particular, for the TVIX Media Center, it can only connect to folders coming off server's root directory.  Thus, make a symbolic link to whatever folder you are going to share.  In my case, I want to share videos under /mnt/lacie/hellanzb/done... so I create a symbolic link to it using the name /tvixhd1.

:/$ sudo ln -s /mnt/lacie/hellanzb/done/ /tvixhd1

An example of verifying the creation of the symbolic link in the / directory on the unix filesystem.

:/$ ls -l | grep tvix
lrwxrwxrwx  1 root root    25 2007-10-02 15:02 tvixhd1 -> /mnt/lacie/hellanzb/done/

We are done the configuration... we now need to restard the portmap and nfs-kernel-server daemons!

$ sudo /etc/init.d/portmap restart
$ sudo /etc/init.d/nfs-kernel-server restart

There are a couple tricks on the TVIX that must be known, as it's no secret the manul is poorly written.  What the TVIX refers to as the server "name" should actually be the server "directory" coming off the NFS-server's root filesystem.  Thus, in our particular setup, it should read "tvixhd1" (without the quotations).  Also, know that in TVIX, the IP Address 192.168.001.055 is the same as 192.168.1.55.  You cannot delete the leading 0s in TVIX.  Furthermore, you cannot specify a particular port to connect through; thus make sure your NFS server is hosting on port 2049 (this is the default).

 There are also several useful commands to run on the NFS server. You...

Can verify what is currently shared with 'sudo showmount -e localhost'.
Can re-export a /etc/export while daemon is running with 'sudo exportfs -ra'
Can check nfs-related ports being used with 'sudo rpcinfo -p' 
Can see transfer/access history of nfs server protocols with 'sudo nfsstat'

---

### Post by pluscool on 2009-06-04
Hello

Thanks for your guide snijper is the best I've found. I have a little problem. When I connect to my ubuntu box I can't see any of the files I supposed to see I have a problem making symbolic links. I just see a folder-icon without a name in the lower part of Tvix GUI in the TV.  

I tested the symbolic link:

:/$ ls -l | grep tvix 

and the results: 

drwxr-xr-x   2 julian root  4096 2009-06-05 22:35 tvixhd1

It didn't show the arrow "path -> path" like in your example:

:/$ ls -l | grep tvix
lrwxrwxrwx 1 root root 25 2007-10-02 15:02 tvixhd1 -> /mnt/lacie/hellanzb/done/

I tried to make the symbolic link several times](*,)](*,)](*,)

any ideas? greatly appeciate! :-s

---

