---
title: "Nautlius! Where are my Desktop icons? Nautilus hangs trying to access Desktop folder"
date: 2008-11-19
forum: General Help
---

### Post by kanin_te_sova on 2008-11-19
Hello. Guess you've heard this all before! I've been looking around.

Something has changed as of today.

I mounted a USB FLASH DRIVE (it was a vFAT I later saw). Yesterday it was OK. I transfered files, even removed some from the USB, freeing up space.

So, this morning, still in a sleepy state, I wanted to delete a movie from the USB - I deleted, went to the trashcan and emtied it!

Now I TRIED to UNMOUNT the device - AND NAUTILUS starts acting weird, kind of hanging itself.

Well, I went to work. Got back home. Restarted and I can still see my icons. But Nautilus was behaving weird. So I go to SYSTEM MONITOR and can se Nautilus (sleeping), I kill it and another Nautilus window pops up! Arghh!!! Killing it again etc. It restarted.... 

Then I killed the Nautilus (Desktop Icon) in SYSTEM MANAGER.

All disapeared. I can still find all my files as SU with Midnightcommander in the Terminal.

Well I log in as root with Nautilus using: gksudo nautilus

Now it CHANGES THE ENTIRE background image (to the default) AND showing ONE icon (backup) on the desktop.

THIS HAS NOT HAPPENED BEFORE!

I was to sleepyheaded this morning - maybe i screwed something up? I think i saw some files ./TRASH in my HOME dir (usually NOT there) I might have deleted, hmm?

It's Nautilus and my USER's config that has broken. Everything else works as it should!

NOW I CANNOT ACCESS ANYTHING, no right-click on the Desktop etc with my USER account. It just starts Sleeping and i have to FORCE QUIT.

In the "processess" tab in System monitor when I start Nautilus it gives me this when hoovering nautilus; "nautilus --no-desktop:///file/home/myusername"

HAVE I deleted this file maybe? How can i restore, reconfigure?

[B]EDIT: Sometimes it hangs and sometimes it doesn't - especially sensitive about the Desktop folder! I can not see the red line.

Well it should be run without the "--no-desktop" normally I guess

Nautilus hangs also when trying to go to my (not root) USER DESKTOP dir while logged in as ROOT? Buuhuuu...

MORE EDITS.... HA HA HA! I logged in as SU in the terminal, ran "nautilus"... Tried to get to my desktop, it hung, BUT - NOW MY DESKTOP ICONS ARE BACK! WTF!!! And I can now see the ("desktop icon") Nautlius running in processes.... 

I'm going to log out reboot an cross my fingers now!

EHHH!!!

EVERYTHING IS BACK TO NORMAL now!!! I don't know what the hell happened here??? But now it's working again.

/EDIT[/B]


[B]EDIT 2: I AM SAD TO SAY. After using the computer for a day - THIS PROBLEM IS BACK AGAIN!

BEATS ME![/B]

Can anyone PLEASE HELP! **EDIT: Or give an explanation maybe?** ;)

I tried reinstalling Nautlius (must have something to do with permissions or some files missing or some config maybe?) but it did not help!


 I have Ubuntu 8.04 latest updates.

Regards

//emil

---

