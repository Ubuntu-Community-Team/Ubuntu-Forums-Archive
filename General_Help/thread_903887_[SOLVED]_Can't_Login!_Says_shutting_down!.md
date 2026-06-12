---
title: "[SOLVED] Can't Login! Says shutting down!?"
date: 2008-08-28
forum: General Help
---

### Post by Calabero on 2008-08-28
Hi there. I know this post is mammoth and i apologize for it, but i feel that i must communicate all information as best i can, and that is unfortunately, an essay :P

As im sure you can already see I am very new to linux...two days new, infact. The latest version of Ubuntu is what i have, and i was attempting to follow the step by step instructions for installing my soundcard found elsewhere on this forum and everything was going great when step 6 was restart your computer.

Well, since i was already performing commands in the terminal, i thought this was a good opportunity to learn a new one. So i typed "man shutdown" to see what i could see, because "restart" is apparently not a valid command :p

So, i try my hand at 'shutdown -r 5' thinking i would get a 5 second countdown which would simply be neat and i made use of another flag. Well then I then realized it was minutes, not seconds, and i had to wait 5 mins before i could restart which i didnt really want to do. I remembered that -c was a flag to cancel so i tried it and nothing happened. I waited ten minutes and everything just sat there, so i flipped the restart button on my computer thinking no harm, no foul as i come from windows XP. Now whenever i try to log into my account, i get an error message saying that "this computer will shutdown in 4 minutes!" or something to that effect, and it prohibits login. I also cannot log into my GUI as root for another reason i dont know because it doesnt like the password i put in even though its my password :S

This has gone on for an hour now, and yes, ive left it alone for much longer than 4 minutes and still no dice. I managed to log in as root on another tty (sorry dont know what its called) and typed startx and continued into GUI and make this post, against the better advice of a message box warning against privileged account use.

I know you are all probably going to smack me up side my virtual head for this, but i feel i must also mention that i did this in su mode, as a friend who is "experienced" in linux (i now know otherwise from the reaction i have received on other forums) told me it would be fine and save me from logging in sudo every command...i am ashamed at my foolishness. Also, i hope there is a solution other than deleting the "josh" user because i just got it set up the way i like it and know i wont remember how to do half of what i just did :P

PLEASE help me! Thank you all soooo much in advance!

---

### Post by Calabero on 2008-08-28
Ah, well it appears as though i have resolved the issue.

For anyone else who may stumble into the same problem as i, the steps i followed are as such:

Upon booting the computer i found myself at my usual GUI login screen. i pressed ctrl+alt+F1 to acheive CLI and logged in as ROOT (dont know why the GUI didnt like it) as root, i typed "shutdown -r 1" for a time of 1 minute and a reboot. 

After boot the issue no longer existed as the root shutdown command killed my other one, i suppose. Do any experienced Ubuntusers have an explanation as to what happened? I would love to learn from my mistakes and appreciate anything you can offer :)

---

