---
title: "Recovering data from a locked ssd with a known password"
date: 2020-05-19
forum: Hardware
---

### Post by RabbitWho on 2020-05-19
Busy people only need to read the stuff in bold: 

I got a splatter of coffee on my lapto[SIZE=2]p,[/SIZE][SIZE=1][SIZE=2] a tiny amount, but I didn't see it, it seeped down all the way through the laptop while it was on, it is dead. I killed it. I am a laptop murderer. :( [/SIZE]
[SIZE=3][SIZE=2]and I had an **ssd password on, that I put on through the laptop bios.** **It's an Elitebook 847**[/SIZE][/SIZE][/SIZE][SIZE=1][SIZE=3][SIZE=2]**0p. As far as I know it has a tpm. **
[/SIZE]
[SIZE=2]Is there anyway I will ever see my data again?[/SIZE][SIZE=1] there's an essay on that drive that took months and write 

[SIZE=2]I've taken everything out to leave it dry, but I've little hope. It was proper permiated, and the fact that it was on...[SIZE=1] my heart is broken. [/SIZE]
[B]
I tried putting the ssd in two other laptops but when I entered the password it said it was incorrect. (it was not). [/B]
I tried using an external reader thingy but that didn't even give me the option to enter the password. 

I know the master password but apparently that only allows me to wipe the ssd and start over, it's the data I want, not the hardware. 

**Is there anything I can do? **

There are some differing opinions here: [https://community.spiceworks.com/topic/1569054-intel-530-ssd-known-password-can-t-unlock](https://community.spiceworks.com/topic/1569054-intel-530-ssd-known-password-can-t-unlock) A person with the same problem. Some told him he was doomed, some told him he just needed a computer that was the same make and model but not broken. Can you shed any light on this? If I shell out on another second hand elitebook from the same year, can I get my data back? [/SIZE][/SIZE][SIZE=2]

I was going to back up and all, i kept meaning to email the essay to myself AND i was planning on upgrading to the new LTS which would have meant backing everything up. So many "if onlys" I also nearly bought a splash proof laptop when i bought this one but the post and packaging was astronomical so I chose this one. 
[/SIZE][/SIZE][/SIZE]

---

### Post by TheFu on 2020-05-19
1,002 reasons to have **daily**, versioned, automatic, **backups**.  Sorry.

This seems like a question for the SSD vendor and Laptop vendor, not related to the OS at all.  For the OS to be involved, there's be LUKS encryption.  You don't mention that and do mention the BIOS being involved.  I'd contact the SSD vendor and check their forums for dealing with this.

If TPM is used, it is likely that the TPM chip AND your password AND the hardware encryption of the SSD are all tied together.  After all, you paid for security and got it.

Whenever encryption is used, having backups is mandatory.  Whenever anything bad happens to encrypted storage, there is usually nothing that can be done to regain access.

---

### Post by Autodave on 2020-05-19
Your chances are little and none.  I offer you one thing which has worked for me occasionally in the past:  hook it up externally to another machine.  Type your password into a text file. When prompted for the pasword, copy and paste the password from your text file.

---

### Post by DuckHook on 2020-05-19
I feel your pain. You can also try taking the whole assembly to a professional data recovery outfit. They charge big money and guarantee nothing, but your work may be worth the expenditure for the admittedly slim chance.

---

### Post by RabbitWho on 2020-05-19
I really wish I had known this was a possibliity. I assumed once I knew my password I could take the drive out and always access the data once the drive was healthy. I feel really stupid for putting a bios password on it now. I'm going to try the professional data recovery people, like you said @duckhook. Thanks for the sympathy :) 

@Autodave When I hook it up externally I don't get any password prompts :( Any ideas on how to get one? 

Same thing happened with my old HDD (except it wasn't my fault the other com broke!) but it didn't matter, it was backed up, i never solved that problem, never understood what went wrong, and if I had I wouldn't have used a bios password again. So may "what ifs".

---

### Post by TheFu on 2020-05-19
We are guessing here.  You haven't posted the exact SSD model or vendor.

Have a friend who trains other data recovery people. 8 yrs ago he wouldn't touch SSDs since there's no way to remove every layer of writes, and eventually, someone will figure out a way to restore each write level. That's his belief.  There are no parts that wear out, just chips go bad.  With on-device encryption, which is what I'm assuming still, even swapping the controller chips or memory chips won't help.  Part of encryption is using a passphrase AND using a unique seed, so that cracking 1 SSD of the model type doesn't mean every SSD for that line is cracked.

As for hardware encrypted SSD storage, doubtful it will ever be accessed, IF the HW is tied into the TPM on a specific machine without using exactly that same TPM.

But if you aren't positive, perhaps it is using LUKS.  With LUKS we can do some things.

**But we need the SSD vendor and model first.**

---

### Post by RabbitWho on 2020-05-22
You'll probably have guessed from my silence that I didn't know the SSD model 

Good news everyone! I un-bricked my laptop. I didn't think I'd even be able to get IPA in the current climate, and I thought it working was a long long shot after how I'd misreated it, but it's better, and I got my essay off it which was THE big thing, but of course there were a million other little things, a lot of heart break, a lot of nausea. Sorry, I'm very long winded. Anyway that's solved, but I can't mark it as solved for future generations wth a similar problem. The closest I got was a data recovery place confirming they wouldn't be able to help me if the TPM was involved but offering to look at it for free to see if maybe it wasn't. 

So now I want to figure out how to make sure it doesn't happen again and have a new thread for the purpose
[https://ubuntuforums.org/showthread.php?t=2443970&p=13959528#post13959528](https://ubuntuforums.org/showthread.php?t=2443970&p=13959528#post13959528)

not being able to access my data again I mean, obviously i'm going to break my computer again, BECAUSE THAT'S WHAT I DO *cries*

---

### Post by TheFu on 2020-05-22
Just above the first post, see that "Thread Tools" button?  Click it, choose "Mark SOLVED" so people don't waste time trying to help something already solved.

Please.

---

