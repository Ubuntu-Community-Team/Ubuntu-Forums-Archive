---
title: "Shutdown / Reboot"
date: 2008-11-16
forum: General Help
---

### Post by fuzzybear3965 on 2008-11-16
Okay so this is my dilemma.. I cannot fall asleep with my computer in the room.  All i need is a terminal command to delay reboot after shutdown or delay reboot with the reboot command.  Can anyone help?

---

### Post by Herman on 2008-11-16
So you want to shut down your computer while you sleep and have it reboot automatically before you wake up, is that what you mean?

I am sure you can have your computer shut down at a certain time with crontab if you want. It would be better to just shut it down manually though, it wouldn't be very nice to have your computer shutting down on you while you're in the middle of something you're trying to finish.

I don't know if you can get it to reboot again once it has been shut down, at least not with any terminal command I'm aware of.
I do know that many computers have a function in the BIOS that you can set to get them to boot automatically at whatever time you specify.
I would take a look around in the BIOS and see if there's something in there for restarting, I think you'll probably be able to do that.

---

### Post by fuzzybear3965 on 2008-11-16
No, i kinow it's possible to restart it with > sudo shutdown -r AND i know you can delay shutdown > shutdown -P +(number of minutes).  However, I was hoping both could be combined so shutdown would be immediate and restart delayed.  My bios has automatic startup features for the date but i have to change the date every day.  THere is no way i can select multiple days for the motherboard to automatically startup... So yeah, i just wanna combine the reboot and shutdown command.

---

### Post by carlhako on 2008-11-22
It cant be done with a command, once the pc is off ubuntu has no control over it, its upto the bios.

If your bios doesn't support turning it on at curtain times like you have stated, you could try wake on lan. Do you have another ubuntu/linux machine running in the house somewhere? You could setup a cronjob to send the wake on lan command to your bedroom pc at a specific time. google "wake on lan linux"

hope this helps

---

### Post by fuzzybear3965 on 2008-11-23
Thank you very much I will look into that.

---

