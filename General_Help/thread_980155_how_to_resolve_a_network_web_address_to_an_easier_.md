---
title: "how to resolve a network web address to an easier name"
date: 2008-11-12
forum: General Help
---

### Post by greavette on 2008-11-12
Hello,

I have a Citadel mail server and an inventory database now running on my own home network.  The paths to each are:

www.<ip of mail>:2000
www.<ip of inventory db>/inventory

I have a router on my network that hands out dhcp and dns.  Is there a way to resolve these addresses to something that is easier to remember like:

mail
inventory

Thanks!

---

### Post by john183 on 2008-11-12
I know in windows you could do things like that by editing the "hosts" file. I am not sure if you can do the same in ubuntu, but you could search the forums for something along the lines of "editing hosts file".

---

### Post by Portmanteaufu on 2008-11-12
If I'm understanding your question properly, you should be able to make a couple of entries in your /etc/hosts file that look like this: 
```

<IP address of mail>:2000                   mail
<IP address of inventory>/inventory         inventory

```

(Other posters feel free to correct my syntax, I'm away from my own computer at the moment.)

If you're asking about always having it keep up with changes in the IP addresses because they're acquired by DHCP, that'll require more work. But if you're administering your home network, you could always set up static IP addresses for the mail and inventory boxes.

---

### Post by greavette on 2008-11-13
Hello,

Thanks for the replies.  I was looking primarily for a solution for my windows PC and had forgotten about the hosts file.  

My router gives out DHCP already and also allows me to set each IP as static (which I do) so my mail and inventory systems are static IP's on my network.

Thanks for the help!

---

