---
title: "Cannot open display through SSH"
date: 2008-07-22
forum: General Help
---

### Post by morningkiran on 2008-07-22
Hi all,
 I am beginer to ubuntu. I installed 8.04. I wanted to do export display from another machine running solaris. 

ssh -X user@<ip of sol machine>

on my pc xhost + 
on solaris export DISPLAY=<ip>:0.0

but i was not able to open xterm. 
Later little googling I tried to change

cat /etc/X11/xinit/xserverrc

from 
exec /usr/bin/X11/X -nolisten tcp
to 
exec /usr/bin/X11/X

and then restarted my pc.
but still the problem exists.

i did a nmap on my pc address I could not find 6000 port open.
Not shown: 1710 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
111/tcp  open  rpcbind
631/tcp  open  ipp
2049/tcp open  nfs

Nmap done: 1 IP address (1 host up) scanned in 11.212 seconds

how can I open display to my machine. I was able to do this on other machines on ubuntu 7 and fedora core machines. 
Please help. thanks in advance,
Udai.

---

### Post by Mister.Vash on 2008-07-22
On the solaris machine do you have in the /etc/sshd_config
"X11Forwarding" and is it set to YES ?  If not, set that and restart sshd on the solaris machine

---

### Post by morningkiran on 2008-07-22
No No... there is no problem in solaris machine I was able to open display on ubunut 7.0 and fedora core .. but not on ubuntu 8.04..

Thanks,
Udai.

---

