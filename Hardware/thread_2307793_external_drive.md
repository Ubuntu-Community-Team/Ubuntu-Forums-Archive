---
title: "external drive"
date: 2015-12-28
forum: Hardware
---

### Post by mrbill4 on 2015-12-28
I am trying to access an external drive and I'm not having any luck. I'm new to Linux and hoping I can find a solution,this drive has a lot of personal info. Thanks for any help.

Okay, the platform version is Kubuntu or KDE 4.13.3
The Harddrive is a WDPSO37RNN 
I don't recall if it's NTFS or FAT32

I apologize if this is the wrong forum or missing info. Please help if you can

---

### Post by Bashing-om on 2015-12-28
mrbill4; OK ... So

Let's see what we can do to determine what it is that we are working with.
With that external drive connected, what returns:
```

sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
as a place to start the troubleshooting from.


[INDENT][INDENT]knowledge is power
[/INDENT][/INDENT]

---

### Post by mrbill4 on 2015-12-28
Nothing returns. I've connected after logging in and from reboot

---

### Post by yancek on 2015-12-28
To clarify, you have Kubuntu on a Live CD or flash drive and you are trying to access another drive, correct?  If you type the command suggested above in a terminal and get no output, that would be very unusual.  Does it not detect your internal drive either?  Can you check the BIOS on boot to see if the external is recognized there?  If not, that isn't good news.

---

### Post by mrbill4 on 2015-12-28
Sorry, I may have mislead you. I have recently loaded Kubuntu on an HP laptop, which  was previously a windows 7 machine. The new software and laptop is running fine and being brand spanking new to the linux world my problem may be ignorance rather than any software or hardware issues. 

The problem I'm having is when I connect the 1 terabyte external western device harddrive to the laptop with Kubuntu installed I do not see it.I am fairly certain that this is an NTFS format.

I am not sure how to enter the above code? Can you instruct me? In the meantime I will reboot to and check BIOS to see if external is recognized, Thanks

---

### Post by Bashing-om on 2015-12-28
mrbill4; Hey .

Not to know is not a sin ! None of us were born knowing. We are happy to instruct.
Please bear in mind I have not seen (k)ubuntu since release 9.04 so I am not familiar with that desk top.
Upon connection of that external drive I would expect an icon to be added to the desk top, and also in the file manager.

To execute the requested terminal command:
At the desktop press the key combo ctl+alt+t to activate a terminal.
in this terminal execute the terminal command:
```

sudo parted -l

``` and copy paste the result - between code tags - back here .

This is but the start of the troubleshooting process - depending on what results is where we look next ( I can feel a dmesg log attack coming on ) .

Hang in here, linux IMHO is the best thing since sliced bread.

[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

### Post by yancek on 2015-12-28
> I am not sure how to enter the above code?

I'm not sure what you are referring to with this comment.  If it is the command:  sudo parted -l suggested above, you should look for the terminal from the K menu in the lower left of your Desktop.  The Ctrl+Alt+t method should also work.  You can check to see if the drive is identified in the BIOS by rebooting the computer and watching the screen on boot for a message telling you which key to press to enter "Setup".

---

### Post by mrbill4 on 2015-12-29
Okay, turns out after trying the external on several computers, I realized I was using the wrong power supply. The external needs 12v and the one I had was only 7v.:oops::oops: Anyway, once I got my hands on a 12 v wall wart I am able to rock the Kubuntu OS. :guitar:Thanks for your help. Now I know just enough to be dangerous. :p

---

### Post by Bashing-om on 2015-12-29
mrbill4; Great !

Pleased you came back and provided the solution.
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThread)

> 
Now I know just enough to be dangerous. 


Never fear, we are here. AND with 'buntu - when you break it you get to keep all the pieces -
[INDENT][INDENT]A liveDVD(USB) can put the pieces back again.
[/INDENT][/INDENT]

---

### Post by mrbill4 on 2015-12-29
Thanks Bashing-om,
How do I mark this thread solved?:confused:

---

### Post by Bashing-om on 2015-12-29
mrbill4; Hey .

No problem, glad to be of assistance.
To mark a thread solved:
1st post -> thread tools drop down menu .
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

