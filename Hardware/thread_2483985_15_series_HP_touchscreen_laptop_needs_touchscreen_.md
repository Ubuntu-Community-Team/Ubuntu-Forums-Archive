---
title: "15 series HP touchscreen laptop needs touchscreen disabled"
date: 2023-02-14
forum: Hardware
---

### Post by shiftfire on 2023-02-14
[SIZE=3]**_The Rundown:_**[/SIZE]         I have a _**15 series HP Laptop**_ currently running _**22.10 on the Kubuntu distro.**_ The problem I'm having is that the **touchscreen defaults my cursor to one a single area of the top of my screen, sometimes at random, mostly it occurs when I adjust the angle of the screen or move the laptop in any way.** It occurs during both times when I have it plugged in/unplugged and gradually gets worse as the battery level decreases. There have been a couple of times now, where I've had to hard reset the computer because I couldn't maintain control of my cursor. 

[SIZE=3][B][U]What I've Tried:
[/U][/B][/SIZE]

[LIST]
[*]Disabling the xinput ID by using terminal to execute "xinput disable (ID)". 
[*]Attempted a udev script to disable the touchscreen on each startup. 
[*]Attempted changing rules.d file as well as attempted creating entirely new rule listing.
[*]Attempted to module blacklist the hid_multitouch module and it did not work. 
[/LIST]

[TABLE="class: grid, width: 1000, align: left"]
[TR]
[TD="align: center"]**Sure Of:**[/TD]
[TD="align: center"]**Unsure Of:**[/TD]
[/TR]
[TR]
[TD="align: center"]The touchscreen can be disabled[/TD]
[TD="align: center"]Whether there is secondary input/output for the interface.[/TD]
[/TR]
[TR]
[TD="align: center"]It cannot be disabled through common input[/TD]
[TD="align: center"]If having both Plasma and Wayland has some effect on the driver.[/TD]
[/TR]
[TR]
[TD="align: center"]If a method is explained, I can execute it properly[/TD]
[TD="align: center"]Why, on windows, I click 1 button to disable the screen and in linux, it's like pulling teeth when the information is so easily accessible to perform the tasks.[/TD]
[/TR]
[/TABLE]

[U][B]Conclusion: ANY AND ALL HELP APPRECIATED
[/B][/U]I've been stumped for awhile now and haven't been able to find any helpful advice as of yet. I've posted for help on the KDE forums, Reddit including multiple subreddits, various ask sites and unfortunately, most posts have just been skipped over. Until today, I was under the impression that one of my posts had been to this forum, but I was wrong ](*,)#-o
Thanks for taking the time to read and I hope to hear from someone soon! Would love to get this situated before my screen decides to short out or some unlucky nonsense.

---

