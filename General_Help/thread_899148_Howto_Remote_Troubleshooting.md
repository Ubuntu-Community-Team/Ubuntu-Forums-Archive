---
title: "Howto? Remote Troubleshooting"
date: 2008-08-24
forum: General Help
---

### Post by justgeig on 2008-08-24
I have helped an increasing number of people shed the Microsoft monopoly in favor of ubuntu/kubuntu and am finding it hard to make time to drive to each person each time they have a linux problem...is there some alternative to LogMeIn? I am running kubuntu only so no windows or mac solutions for me :-)

---

### Post by Stemp on 2008-08-24
VNC ? vino for gnome and I think it's Krfb for Kubuntu.

---

### Post by justgeig on 2008-08-24
I am very familiar with vnc's but how viable is it to do that for computers outside of my own network?

---

### Post by Stemp on 2008-08-24
[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

Using ssh port-forwarding is of course far more secure. 
The only problem is to get the IP of your friends. You might want to create some dyndns or no-ip adresses for them.

---

### Post by justgeig on 2008-08-24
Ok I follow the dyndns but not no-ip addresses.....and would it be secure to just have them go to whatismyip.com and give me their ip address each time they need help? I would of course set kfrb up to only allow connections after they have been confirmed

---

### Post by Stemp on 2008-08-24
Yes sure you could do that. That's usually what I'm doing in fact.

---

### Post by justgeig on 2008-08-24
Ok awesome, I think that would be easiest....is there any setup as far as their router would go? Port forwarding and whatnot lol

---

### Post by Stemp on 2008-08-24
No port forwarding on their side, just opening port 5900 and installing OpenSSH.
Nearly everything is done on your side.
Check the documentation it's pretty easy.

---

### Post by justgeig on 2008-08-24
wow thanks a bunch!

---

