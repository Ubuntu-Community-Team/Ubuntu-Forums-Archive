---
title: "how to unmount ex.HDD with running Ubuntu?!"
date: 2010-04-05
forum: Hardware
---

### Post by ujodarko on 2010-04-05
Hi :)

I makes things complicated ;) so I installed Ubuntu on external 2.5" USB HDD :D that is powered only by USB port! It works just fine, but I am wondering... how to turn off that HDD properly > without that sharp power cuting off. Is there chance to make HDD unmount second before computer stays out of power?

I am scared that by the time that HDD is going to die because of that irregular turning off.

Off course, HDD is not visible on desktop as it is system drive ;)

---

### Post by pastalavista on 2010-04-05
When the OS calls for a system shutdown, it automatically unmounts all the drives. What "irregular turning off" do you mean?

---

### Post by ujodarko on 2010-04-05
> **pastalavista said:**
> When the OS calls for a system shutdown, it automatically unmounts all the drives. What "irregular turning off" do you mean?

Yes, it unmounts all drives that are visible on the, lets say, desktop. But, it cannot umnount drive that is system drive. Can Ubuntu unmount internal HDD from system although it runns from that drive? I don't think that's possible.

Irregular turning off?

When I phisically pull eksternal HDD cable from the USB that is powering the same HDD, I hear sound from HDD that is very similar to breaks of deaccelerating car. The same sound is produced when I turn Ubuntu by choosing 'shutdown' from menu.

I am sure that Ubuntu at this stage is turning eksternal drive 100% irregulary way because, if I use that disk under XP, and choose 'safe remove hardvare', that sound does't occur.

What I need is a way to safely spin down that external Ubuntu host drive before it looses power. Do you have any idea?

---

### Post by pastalavista on 2010-04-05
Since Ubuntu is mounted on the external USB drive, it would be the last thing shut down and wouldn't "spin down" normally, but it is unmounted properly. The noise is because the power goes off before it stops spinning. I don't believe that harms it in any way. I could be wrong.

---

### Post by ujodarko on 2010-04-05
God knows... but there is diference in sound when disk is ejecting from XP by 'safely removing hardvare' and shutting down under Ubuntu.

'Ubuntu' sound is like car breaks :-? (aldough much more silent), but XP shuts down HDD without any sound :)

You said: The noise is because the power goes off before it stops spinning

So... is it possible to stop disk and then cut off power?

---

### Post by pastalavista on 2010-04-05
try rebooting Ubuntu this way... hold down Alt+SysRq(PrtSc) and press individually in this order R,S,E,I,N,U,B

The hard drive should be unmounted after the U so let it spin all the way down before pressing the B.. which reboots

---

### Post by ujodarko on 2010-04-05
?

Interesting, I'll try.
How to shut down?

What does R,S,E,I,N,U,B stands for? 

Thanks!

---

### Post by pastalavista on 2010-04-05
From [this page]("http://en.wikibooks.org/wiki/Linux_Guide/Freezes"):

> Alt+SysRq+ 	Action 	Uses
R 	UnRaw 	Turns off keyboard raw mode. This allows input from the keyboard even if X-Window has crashed.
K 	SAK - Kill all on console 	Secure Access Key - Kills all programs on the current virtual console. This is useful if you want to make sure there are no programs waiting on the console to grab your password, or if a process won't let you switch consoles.
S 	Sync 	Attempts to sync all filesystems. This lessens the chance of data loss and fscking. Syncing is complete when "done" or "OK" is printed.
U 	Umount 	Attempts to remount all filesystems as read-only. Umounting is complete when "done" or "OK" is printed.
B 	Reboot 	Will immediately reboot without syncing or unmounting any disks. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
C 	Crashdump 	Will perform a kexec reboot, in order to take a crashdump. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
O 	Power Off 	Turns off the computer without syncing or unmounting disks. Before using this use Alt+SysRq+S and Alt+SysRq+U to avoid data loss.
P 	Show Pc 	Attempts to dump all registers and pointers to console.
T 	Show Tasks 	Attempts to dump a list of all tasks to console.
M 	Show Memory Info 	Displays memory info to console
V 	Voyager processor info 	Dumps Voyager SMP processor info to your console.
0-8 	Kern&#1077;l Error Verbosity 	Set the console log level for kernel messages. Setting to 0 only shows messages like PANIC and OOPS
F 	OOM Kill 	Calls oom_kill to kill a memory hog process
E 	Term 	Sends SIGTERM signal to all processes.
I 	Kill 	Kills (sends SIGKILL signal to) all processes.
L 	Kill + Kill Init 	Kills (sends SIGKILL signal to) all processes, including init. You will not be able to do anything else after using this!
N 	Nice 	Make real-time processes nice-able.
H 	Help 	Prints some help

edit: to shut down instead of reboot, replace the 'B' with 'O'

---

### Post by ujodarko on 2010-04-06
> **pastalavista said:**
> From [this page]("http://en.wikibooks.org/wiki/Linux_Guide/Freezes"):



edit: to shut down instead of reboot, replace the 'B' with 'O'

no, there is sound again :-?
Something else...to try?

---

### Post by pastalavista on 2010-04-06
> **ujodarko said:**
> no, there is sound again :-?
Something else...to try? I'm guessing you installed the boot sector on the USB drive? Can you boot it up on any other computers? Maybe if you had /boot or swap installed on the HDD it would help. I'm all out of ideas, sorry.

---

### Post by ujodarko on 2010-04-06
> **pastalavista said:**
> I'm guessing you installed the boot sector on the USB drive? Can you boot it up on any other computers? Maybe if you had /boot or swap installed on the HDD it would help. I'm all out of ideas, sorry.

Don't be sorry, you helped gaveing me some ideas...

I am thankfull!

---

