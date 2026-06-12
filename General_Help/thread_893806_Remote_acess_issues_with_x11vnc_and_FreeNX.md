---
title: "Remote acess issues with x11vnc and FreeNX"
date: 2008-08-18
forum: General Help
---

### Post by Cata1yst on 2008-08-18
Hey all

Still trying to work out the kinks on my server...and remote acess is the nail thats sticking out. I have both x11vnc and FreeNX installed.

With x11vnc i have to run > x11vnc -usepw everytime i want to remotely connect.... im missing something here...is there something i need to do? any workaround so that i dont have to do this everytime i want to remote connect?

Edit: i got FreeNX to connect...reset all the keys...
> sudo dpkg-reconfigure freenx-server
then remove keys...run it again and set custom key
> sudo cp /var/lib/nxserver/home/.ssh/client.id_dsa.key /home/(user)/Desktop
sudo chmod 644 /home/user/Desktop/client.id_dsa.key
ported it through samba and imported it to my NX client

now to get xfce working with NX client...anyone done it yet?
Edit: Solved...Run the NX server install instead of freenx...use latest windows client under custom display settings....and tell it to "startxfce4"
Oliver

---

### Post by prince_niceguy on 2008-08-19
please mark the thread as solved from thread tools to help others.

---

