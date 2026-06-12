---
title: "Linux/Windows Dual boot-No virus protection?"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by MrChips on 2006-01-02
I am planning on starting a new config for one of my computers.  To go down the list:

1.It will have a dual boot, Windows for gaming, Linux for web browsing and all else.
2.It will be on a small LAN network with dialup as means of connecting to the internet.
3.And I do not plan on installing virus protection as my Windows setup will be simplified for graphic performance and WILL NOT connect to the internet.

Question is...will the Windows boot section and file system be vulnerable to viruses if I only use Linux to browse the web.

Or would it be safer to have them on separate hard drives rather than spliting the partition on one drive.

---

### Post by john_spiral on 2006-01-02
Hi,

If your windows game system can mount your Linux partition then I would worry about firewalling and virus protecting windows, if not, and it's not connected to a network who cares if your game system runs wild with virus junk.

my 3 cents

Johne

---

### Post by socrazy143 on 2006-01-02
I'd say you are pretty safe but for kicks you could load Avast Anti-Virus (Free!) and use Spybot's Tea Timer to protect the registry.  I would assume that you have SP2 (Service Pack 2) so you should have a smokescreen (let's be honest the XP firewall is NOT much of a firewall).

---

### Post by Zelut on 2006-01-02
In my opinion if you NEVER connect windows to the internet you're perfectly safe but I'll bet you $1000 that the first time you do connect using XP you get a virus.

..just make sure all of your browsing, chatting, ANY connecting is done thru linux and you should be fine.

---

### Post by Sef on 2006-01-02
Also another free anti-virus is AVG by grisoft.

---

### Post by Herman on 2006-01-02
> I am planning on starting a new config for one of my computers.  To go down the list:
1.It will have a dual boot, Windows for gaming, Linux for web browsing and all else.
2.It will be on a small LAN network with dialup as means of connecting to the internet.
3.And I do not plan on installing virus protection as my Windows setup will be simplified for graphic performance and WILL NOT connect to the internet.
Question is...will the Windows boot section and file system be vulnerable to viruses if I only use Linux to browse the web.
Or would it be safer to have them on separate hard drives rather than spliting the partition on one drive. MrChips,
You have a great idea! That's the way I do it.

The first thing most of us do is get rid of the old boot sector by overwriting it with the first stage of our GRUB boot loader. Then I don't think you'll have to worry about that anymore! That should fix it!

The Windows system itself will always be vulnerable to viruses* **if** *you move files into it that might contain viruses. 
If you ***don't*** import anything into Windows that might contian a virus or spyware, either from the internet or a CD, then no spyware or virus can get into Windows. Even if one does, and you only have games in Windows, and not irreplaceable files, you can easily just re-install those.

There is no need to have the systems on two seperate hard drives.

If you use Ubuntu for all your internet work, like collecting email, and browsing the web, you will be safe. You can also use Ubuntu for all your important files. Of course, you should also have any valuable and irreplaceable files backed up on some other media regardless of your choice of operating system.

You will still probably need a firewall for Windows unless you physically unplug your internet wire every time you boot Windows. That's easy to do if you rig your wiring up right for it so you have some plugs that are easy to reach.
:D (Herman)

---

### Post by MrChips on 2006-01-02
Great!  Thanks for the response.  
Although I know that it would not be 100% safe.  I am willing to try it out.  I do use Avast on my other machines and it works well, so if I can isolate XP in it's partition on the hard drive I'll go with it.

The ONLY thing I plan on using Windows for on the comp is games.  Being that I am on Dialup and am **still** trying to connect through Linux (I refuse to give up).  I still need time to tinker with it, but would like a little R&R on the side. ;) 

Until I can download Wine or Cedega to play the few games I have, I will use Windows just for that purpose.  I am using Ubuntu but plan to try other distros if it doesn't pan out with the 56k.

Although having DSL would make it easier...:)

---

### Post by LoclynGrey on 2006-01-02
I'd put something like zone alarm on your windows set up and block all port traffic.

---

### Post by Ptero-4 on 2006-01-02
And backup the saved progress files for your games. You don't wanna have to beat all those bosses again just b/c a nasty virus killed your progress files.
P.S: Those file's locations and names depend on the games you have.

---

