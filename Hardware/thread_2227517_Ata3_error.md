---
title: "Ata3 error"
date: 2014-06-02
forum: Hardware
---

### Post by bjarkesmortensen on 2014-06-02
Hey everybody.
I'm very new to Ubuntu, and yesterday I managed to do something incredibly stupid. While I was tweaking Gnome, I wanted to use compizconfig, which I had from when I was running Unity. Since I couldn't understand, why it wasn't responding I turned to google and found a page, where it was recommended that I use "compizconfig --replace" in terminal. I did that, and then the interface dissapeared exept the terminal, which at somepoint froze. Then I did a hard reboot. Since then every time I enter ctrl+alt+F1 I get the following errormessage running over and over again:[INDENT]Ata3: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Ata3: irq_stat 0x00000040, connection status changed
Ata3: SError: { DevExch }
[/INDENT]

Sometimes it changes a bit to the following before switching back:[INDENT]Ata3: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
Ata3: irq_stat 0x00000040, connection status changed
Ata3: SError: { Commwake DevExch }
[/INDENT]

I have tried the reinstalling Ubuntu Gnome, and also downloaded Gnome disks and ran a SMART test on my drive, which came out with a disk "o.k.". I am using Ubuntu Gnome 14.04 on a Lenovo 570G. I am not experiencing any problems besides those errormessages (yet...).

---

