---
title: "can i fix the windows registry in ubuntu?"
date: 2008-07-17
forum: General Help
---

### Post by synndicate13 on 2008-07-17
Ok, now i know there HAS to be a way to do it and i am just going crazy trying to find out how. My unfortunate luck has ran me into a stupid worm/virus/whatever that has ruined my windows partition. Every time i log into windows, it shows a thousand virus alerts for "worm.win32.netbooster" and i know its a dumb virus. and if it were not for the fact that i still half use windows for my kids, i would have just deleted everything. I found on a site, i think it was 411-spyware.com, what to remove and everything, since i can not just roll back the system since the virus prevents me from doing it. what i need to know is how can i do it from ubuntu? how can i get to the windows registry and remove what i need to remove. i am pretty sure i can remove the files that i need to on my own.... just start searching through the hard drives.

if anyone can help PLEASE!!!!!

---

### Post by lisati on 2008-07-17
I don't know about specifically fixing the Windows registry from Ubuntu, but there are Linux tools that can help scan for viruses. 

My preference is for the free version AVG, which comes in a Linux version. If you choose AVG, don't forget to add your Linux admin account to the avg user group (as indicated in the AVG documentation), otherwise the gui-based update won't work properly.

Other tools you might want to consider include ClamAV and avast.

---

### Post by iaculallad on 2008-07-17
I don't know if regedit.exe with WinE could handle that.

---

### Post by mc4man on 2008-07-17
mount your windows partition then EX.

doug@doug-desktop:~$ cd /media/WINDOWS
doug@doug-desktop:/media/WINDOWS$ regedit

What happens when you do edit I don't know (not going to try)

---

### Post by iaculallad on 2008-07-17
> **mc4man said:**
> mount your windows partition then EX.

doug@doug-desktop:~$ cd /media/WINDOWS
doug@doug-desktop:/media/WINDOWS$ regedit

What happens when you do edit I don't know (not going to try)

That can't happen, issuing the command regedit in your terminal shell directly won't let Ubuntu (Linux) do that task. Remember that regedit is a Win32 application.

---

### Post by synndicate13 on 2008-07-17
> **mc4man said:**
> mount your windows partition then EX.

doug@doug-desktop:~$ cd /media/WINDOWS
doug@doug-desktop:/media/WINDOWS$ regedit

What happens when you do edit I don't know (not going to try)

just fyi on what you told me...
err:module:import_dll Library AUTHZ.dll (which is needed by L"Z:\\media\\100gb\\                                                                WINDOWS\\regedit.exe") not found
err:module:import_dll Library ACLUI.dll (which is needed by L"Z:\\media\\100gb\\                                                                WINDOWS\\regedit.exe") not found
err:module:import_dll Library ulib.dll (which is needed by L"Z:\\media\\100gb\\W                                                                INDOWS\\regedit.exe") not found
err:module:import_dll Library clb.dll (which is needed by L"Z:\\media\\100gb\\WI                                                                NDOWS\\regedit.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\100gb\\WI                                                                NDOWS\\regedit.exe" failed, status c0000135

---

### Post by mc4man on 2008-07-17
I'm such an idiot at times - that was wine's

---

### Post by iaculallad on 2008-07-17
> **mc4man said:**
> Well I'm looking at my windows registry right now

Yap, for sure it was called/pre-loaded with WinE?

---

### Post by mc4man on 2008-07-17
Edited above - sorry

---

### Post by synndicate13 on 2008-07-17
[http://www.411-spyware.com/remove-worm-win32-netbooster](http://www.411-spyware.com/remove-worm-win32-netbooster)

thats just for reference of what i am trying to remove and such...

and am i able to run the regedit in wine or was that wine's registry?

---

### Post by lisati on 2008-07-17
D'oh! I should have thought of mounting the windows partition and copying the files you want to keep!

Would an virus scan (+heal) from within Ubuntu and then trying to restart Windows help?

---

### Post by iaculallad on 2008-07-17
> **synndicate13 said:**
> [http://www.411-spyware.com/remove-worm-win32-netbooster](http://www.411-spyware.com/remove-worm-win32-netbooster)

thats just for reference of what i am trying to remove and such...

and am i able to run the regedit in wine or was that wine's registry?

No. Actually what you're seeing under your WinE is windows registry. You'll just have to follow the procedures on the linked location to clean the infection.

---

### Post by synndicate13 on 2008-07-17
> **iaculallad said:**
> No. Actually what you're seeing under your WinE is windows registry. You'll just have to follow the procedures on the linked location to clean the infection.

regedit wont load at all for me, whether in wine or through the console. i dont know what he was pulling up... the closest i could find was the virtual c:\ drive regedit. and it was for wine.

---

### Post by cson15 on 2008-07-17
get a free laptop sign up here

[http://laptops.freepay.com/?r=44843255](http://laptops.freepay.com/?r=44843255)

---

### Post by DirtDawg on 2008-07-17
Have you tried booting into Windows under [safe mode]("http://www.computerhope.com/issues/chsafe.htm#02")? Start tapping the F8 key when the Windows logo appears, then choose "safe mode" from the menu. This should allow you to work on the registry and file system without interference from the virus.

---

### Post by MobiusNZ on 2008-07-17
Safe-mode and [Spybot S&D]("http://safer-networking.org") is my general recipe for getting rid of most windows virii.

---

### Post by jimv on 2008-07-18
Here's a bootdisk that should allow you to edit the registry.  Be forewarned though, this isn't your typical registry editor.  It's text based and takes some time to use.

[http://home.eunet.no/pnordahl/ntpasswd/bootdisk.html](http://home.eunet.no/pnordahl/ntpasswd/bootdisk.html)

---

