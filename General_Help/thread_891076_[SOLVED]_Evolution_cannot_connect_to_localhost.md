---
title: "[SOLVED] Evolution cannot connect to localhost"
date: 2008-08-15
forum: General Help
---

### Post by peruvianfreak250 on 2008-08-15
hello everyone, im trying to setup ypops so i can use my yahoo mail account with evolution or thunderbird. I installed ypops and i think i set it up correctly because i followed these instructions

[http://www.geocities.com/t_skariah/ypops/]("http://www.geocities.com/t_skariah/ypops/")
even used the same ports and stuff.

however when i try to receive email in evolution it gives me an error saying
"Could not connect to localhost: Connection refused"

I'm thinking maybe something is blocking ypops from working right, anyone got any idea of what it could be?

---

### Post by peruvianfreak250 on 2008-08-16
bump

---

### Post by heartburnkid on 2008-08-16
You might need to open up the ports used by YPOPs on the firewall; go to terminal and enter the following:

```
sudo ufw allow 5110
sudo ufw allow 5025
```

That should open the ports for POP3 and SMTP access.

---

### Post by peruvianfreak250 on 2008-08-16
tried that and restarted ypops but it still didnt work
:(

---

### Post by IndieInvader on 2008-08-16
I have the same problem, except that I'm using thunderbird but I imagine that it won't make much difference, we *are* getting the same error after all. I have a content filter (Firehol, Dansguardian, and Tinyproxy) installed, could that be affecting anything.

---

### Post by peruvianfreak250 on 2008-08-21
nvm guys. a WHOLE bunch of googling for alternatives to ypops made me stumble upon this

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

its an addon to thunderbird that lets you connect to Yahoo, Hotmail, Lycos (Europe), MailDotCom, Gmail, Libero, and AOL.

---

### Post by peruvianfreak250 on 2008-08-21
oh and when you download the yahoo extension you have to use preferences and choose beta.

---

