---
title: "Small linux cluster/lab"
date: 2008-08-25
forum: General Help
---

### Post by sricketts on 2008-08-25
A year ago my company (~20 employees) had one linux machine, and now we have three. As the number of machines and users grow, it seems like we need to take a careful look at the configuration of our small linux "cluster" or "lab" (I am not sure what the right word would be here).

The linux machines will be used mostly by coders. Since the machines are different, users will often want to jump between machines. For example, one machine has a GPU that we use for prototyping GPGPU codes written with CUDA, while another has a virtual machine necessary to run one of our in-house software tools.

I am curious what kinds of things we may need to start looking into. Here are some examples:

- It would be nice to give each user a single account that can be authenticated and managed transparently from any machine. It seems LDAP might work here, but is it ideal?

- Similarly, I would like to have a shared filesystem so that at least a user's home directory looks the same on all machines. One solution would be an NFS server.

- What if I want to install software across all of the machines? Is there a tool that can make this process more automatic than running the same apt-get install command on each machine?

A challenge is the sort of ad-hoc nature of the setup. The hardware is different across machines. To keep things simple I could make the linux distro the same across machines -- is ubuntu a good fit?

There might be other features I should consider that others have discovered to be helpful. I would love to hear about them.

Clearly I am a bit of a novice in this area, so I am not too confident. Any pointers as I craft a plan would be helpful. I want to make sure that I am headed in the right direction before I dive into tutorials and start implementing.

Thanks,
Scott

---

### Post by linuxuser42 on 2008-08-28
> **sricketts said:**
> 
- It would be nice to give each user a single account that can be authenticated and managed transparently from any machine. It seems LDAP might work here, but is it ideal?

At our company (100 Users) we use both Active Directory with winbind and NIS for this.

> 
- Similarly, I would like to have a shared filesystem so that at least a user's home directory looks the same on all machines. One solution would be an NFS server.

... and in my view the best solution, still. 

> 
- What if I want to install software across all of the machines? Is there a tool that can make this process more automatic than running the same apt-get install command on each machine?

A challenge is the sort of ad-hoc nature of the setup. The hardware is different across machines. To keep things simple I could make the linux distro the same across machines -- is ubuntu a good fit?

Yes. I would use the diskless ubuntu howto: [http://wiki.ubuntu.com/DisklessUbuntuHowto]("https://wiki.ubuntu.com/DisklessUbuntuHowto"). It works for us - now on second year. We run  many lab machines, VMware clients and workstations with different hardware this way having only to maintain a few master installations.

I also recommend that you make /etc unique for each machine using e.g. unionfs. We make a 30MB loopfile under /cfg/<mac-address>/loopfile and mount that on top of /etc using unionfs. This is done in /etc/init.d/checkroot.sh.

> 
Clearly I am a bit of a novice in this area, so I am not too confident. Any pointers as I craft a plan would be helpful. I want to make sure that I am headed in the right direction before I dive into tutorials and start implementing.

- a good network towards the nfs server
- backup the master image on the nfsserver before each maintenance step
- new things to do - now you dont have to update 20 machines but just one ;-)

---

### Post by sricketts on 2008-08-28
Thanks for the pointers -- I will take a look.

---

