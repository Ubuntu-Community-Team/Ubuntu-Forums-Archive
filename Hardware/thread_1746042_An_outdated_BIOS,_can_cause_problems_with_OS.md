---
title: "An outdated BIOS, can cause problems with OS?"
date: 2011-05-01
forum: Hardware
---

### Post by martincasc on 2011-05-01
Hi folks, a lot of time since my last post here. How are you doing? I'm having a problem that **don't let me install Ubuntu 11.04 on my Desktop PC**. Actually it's with Lucid, but I want to goes to natty.u

I use "all variants" prefix 'cause, at first, I thought It was an Ubuntu problem's only, but then I've tried with Carkra and the same kernel's version: 2.6.38 and I have the same problem.

I'm using [*[COLOR="Blue"]askubuntu too[/COLOR]*]("http://askubuntu.com/questions/35129/couldnt-load-ubuntu-natty-beta-1-2-32-64-bits-from-liveusb-on-my-desktop-p") for trying to solve the problem.

My desktop machine it's a C2D, with 2gb of RAM and and nvidia graphic card 6600 and a [*[COLOR="Blue"]ASUS motherboard[/COLOR]*]("http://www.asus.com/Motherboards/Intel_Socket_775/P5PEVM/").

Since Ubuntu Natty it's using 2.6.38 kernel, when I try to load de live session I don't see the plymouth. Instate I see something like a terminal. But doesn't load anything, I can let it 1, 2 or 3 hours and nothing happen...

That,s with the nvidia graphic card on.

When I use onboard graphic card the live sessions loads, but with a lot of problems, graphic problems, and crashes. It seems that load a desktop with some 3d effects instate of compositing manager. It doesn't load Unity, instate de classic session, with 2 panels, 4 desktops and a lot of bugs, shadows and so on.

If I try to open a menu or a windows, I see a black square instate of the menu or the windows. I can't shot down the PC normally. If I open 2 wondows, one of them it's always on top, even if I minimize it.

Thinking that was an LiveUSB problem (see CYREX's answer on askubuntu's link), I've burn a LiveCD, and same problem. Then I've tried with Chakra Linux, with the same kernel: 2.6.38. And it's work fine with the onboard video, not with nvidia card.

So I thought it was an Ubuntu's problem. But then I've tried to load some desktop effect, on Chakra, and guess what? Same problem that on Ubuntu.

So, I conclude that maybe there is some incompatibilities between this new version of the Kernel an my motherboard.Specially when trying to use some desktop's effects.

One note. My motherboard is an [*[COLOR="Blue"]ASUS P5PE-VM[/COLOR]*]("http://www.asus.com/Motherboards/Intel_Socket_775/P5PEVM/"). According the booting screen, my motherboard's revision it's 0801; according the printed REV on motherboard, the REV is 1.øø. According to ASUS web, fully support for C2D starts with 1201 REV. (I have an error at booting, but let me use normally Lucid Lynx, and Maverick when I've tried it from a LiveUSB). A friend and technician told me that the booting error was 'cause the outdated Bios.

Googling [*[COLOR="Blue"]I have this[/COLOR]*]("http://vip.asus.com/forum/view.aspx?id=20110417224456867&board_id=1&model=M4A89GTD+PRO%2FUSB3&page=1&SLanguage=en-us"). That user have same problems with the same OS, same Mother. But' his BIOS it's update.

Anyway, my question is: An outdated BIOS can cause problems with, in this case, Ubuntu 11.04?

I'm thinking in update my BIOS, but I know its a little risky an I'm not sure with the steps for it. So, I want to be sure that an outdated bios it's causing me troubles before take the risk and update the BIOS.

Martín.:p

---

