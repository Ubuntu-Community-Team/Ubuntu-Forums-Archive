---
title: "Any Smartstep 100n users?"
date: 2008-06-25
forum: Hardware
---

### Post by NoSmokingBandit on 2008-06-25
Someone gave me an old dell smartstep 100n with xp on it, so i formatted and tried to install fluxbuntu 7.10 on it, and it installs fine, but when i try to boot the system it gets all glitchy after the screen with the round symbol thing on it (the white screen with the fluxbox logo).
It works perfectly up until that point, then the screen gets all weird and stuff and it doesnt work at all.
I can boot into the recovery mode and it works fine from the terminal, but the gui doesnt seem to function well. Any ideas?

---

### Post by snowpine on 2008-06-25
> **NoSmokingBandit said:**
> Someone gave me an old dell smartstep 100n with xp on it, so i formatted and tried to install fluxbuntu 7.10 on it, and it installs fine, but when i try to boot the system it gets all glitchy after the screen with the round symbol thing on it (the white screen with the fluxbox logo).
It works perfectly up until that point, then the screen gets all weird and stuff and it doesnt work at all.
I can boot into the recovery mode and it works fine from the terminal, but the gui doesnt seem to function well. Any ideas?

Hi Bandit, the following worked for me when my new Fluxbuntu install stalled at the "clock screen;" it is certainly worth a try. (Note, though that I don't have the Smartstep; mine is a Dell Latitude Cpx.)

   1.  Restart the computer and wait for Grub to appear.
   2. You will have 3 seconds to press esc to for Grub options.
   3. Press 'e' to edit the first line that starts 'Ubuntu 7.10 kernel'.
   4. Scroll down to the second line that starts with 'kernel' and press 'e' to edit it.
   5. Delete the word 'splash' at the end of the line.
   6. Press Enter.
   7. Press 'b' to boot.
   8. You'll see a series of text messages instead of the white screen. Hopefully, a login screen will appear! If so, proceed with these instructions to make the change permanent. If not, sorry! :(
   9. Once logged in, double-click the Console icon at the top left and type:
      ```
sudo nano /boot/grub/menu.lst
```
  10. Delete all instances (2 by my count) of the word 'splash'
  11. Save the file by Ctrl+O, then Enter.

---

### Post by NoSmokingBandit on 2008-06-25
I tried removing "splash" but instead of getting stuck at a glitchy srceen it got stuck at a plain black screen, lol.
Thanks for the effort though.
If i cant get this figured out i might just try installing Hardy Heron on it. The pos only has 128mb ram though, so i'll have to tweak the daylights out of gnome, but it will be fun regardless.
Anyway, if anyone has any other ideas i am open for suggestions :)

---

### Post by snowpine on 2008-06-25
> **NoSmokingBandit said:**
> I tried removing "splash" but instead of getting stuck at a glitchy srceen it got stuck at a plain black screen, lol.
Thanks for the effort though.
If i cant get this figured out i might just try installing Hardy Heron on it. The pos only has 128mb ram though, so i'll have to tweak the daylights out of gnome, but it will be fun regardless.
Anyway, if anyone has any other ideas i am open for suggestions :)

Sorry that didn't work for you, Bandit, so let me give you one more tip: You can "roll your own" alternative to Fluxbuntu [by following these instructions]("http://www.psychocats.net/ubuntu/minimal#barebones"). Those instructions are for icewm, however, you can substitute fluxbox instead of icewm. The idea is to install just the bare bones, then add only the applications you need. Just a suggestion.

---

### Post by NoSmokingBandit on 2008-06-26
I dont have internet access on the poor lappy, it has no built-in wifi. I have a wusb54g usb dongle, but i've never seen that work OTB and i am not good enough to get it working from the terminal.
Ill see what i can do though, thanks for the help!

---

### Post by snowpine on 2008-06-26
> **NoSmokingBandit said:**
> I dont have internet access on the poor lappy, it has no built-in wifi. I have a wusb54g usb dongle, but i've never seen that work OTB and i am not good enough to get it working from the terminal.
Ill see what i can do though, thanks for the help!

I have the wusb54g as well! It will not work ootb, but there are some good guides here on the forums.

This thread discusses a couple of the possibilities: [http://ubuntuforums.org/showthread.php?t=827473](http://ubuntuforums.org/showthread.php?t=827473)

And this is the method that worked for me:
[http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

Once I followed those instructions, I added an application called 'rutilt' and I use that to set up my network. There are some workarounds!

---

### Post by NoSmokingBandit on 2008-06-26
oddly, pclos installed fine (i had a disc laying around). Odd seeing as its kde-based. I installed XFCE and it actually runs fairly well other than the fact that RPM distros suck compared to DEB ones. I tried the 6.60-7.10 ubuntu discs but none of them booted at all. Ubuntu must not like my lappy. Oh well, all is working fine now. Thanks a ton, i appreciate it.

---

### Post by NoSmokingBandit on 2008-07-06
Woot. I got the minicd to boot and install. Its boots up and i see the loading screen with the orange progress-bar thing, then the screen kinda freaks out on me. I hear the welcome sound (the bongos or w/e it is) but the screen gets all weird and glitchy and gives me kind of random vertical lines of color.
I booted into recovery and ran the Fix X Server thing and it didnt really do a whole lot. Any ideas?

edit:
After resetting the XServer a billion times it went into low-graphics mode and seems to work good so far. Other than the fact that its in low-graphics mode, that is.
I think its the intel i915 chipset. How do i get full resolution?

---

