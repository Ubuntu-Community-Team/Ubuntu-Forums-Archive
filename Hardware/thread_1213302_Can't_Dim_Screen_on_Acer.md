---
title: "Can't Dim Screen on Acer"
date: 2009-07-14
forum: Hardware
---

### Post by trentscott4 on 2009-07-14
I have an Acer Aspire One A0751H netbook and cannot dim the screen brightness.  My function keys do bring up the slider, but it doesn't adjust the brightness of the display when I move it.  Any thoughts?

---

### Post by guushoekman on 2009-09-26
> **trentscott4 said:**
> I have an Acer Aspire One A0751H netbook and cannot dim the screen brightness.  My function keys do bring up the slider, but it doesn't adjust the brightness of the display when I move it.  Any thoughts?

I have an Acer Aspire 4736 and the exact same problem. Have you found a solution yet?

---

### Post by zoexii on 2009-11-11
Me too.  
still no luck?
> **trentscott4 said:**
> I have an Acer Aspire One A0751H netbook and cannot dim the screen brightness.  My function keys do bring up the slider, but it doesn't adjust the brightness of the display when I move it.  Any thoughts?

---

### Post by akannankeril on 2009-12-21
ditto
one of the problems i am facing with ubuntu. the fn keys works and the slider moves but no actual change on the brightness.. its spoiling my eyes!!!

---

### Post by akannankeril on 2009-12-29
i think i found a workaround to this one

thanx to Ricardo Schmidt in [http://www.linlap.com/wiki/acer+aspire+5738]("http://http//www.linlap.com/wiki/acer+aspire+5738")

just edit your grub file from /etc/default/grub
you will find a line
 GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
  change it to
 
   GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux acpi_backlight=vendor” 
you need to log in as root to edit this file

for all you novices like me i will try to give you a step by step
open your console (for kde, go to start button >systems> terminal)
$ type "**gksudo dolphin**" 
or type "**gksudo nautilus**"
this command brings up your default file explorer. you will be prompted for your admin password.

once password is entered the explorer windows will come up. go to /etc/default/ open file called grub. it will be automatically opened in an editor
find the line 
 GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
   change it to
  
    GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux 

save the file and close
on terminal, type sudo update-grub
then reboot


now the screen brightness would be working fine
btw in mine fn+rght arrow will decrease the brightness(just the reverse)


hope this was some help

---

### Post by kstannard on 2010-04-25
> **akannankeril said:**
> i think i found a workaround to this one

thanx to Ricardo Schmidt in [http://www.linlap.com/wiki/acer+aspire+5738]("http://http//www.linlap.com/wiki/acer+aspire+5738")

just edit your grub file from /etc/default/grub
you will find a line
 GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
  change it to
 
   GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux acpi_backlight=vendor” 
you need to log in as root to edit this file

for all you novices like me i will try to give you a step by step
open your console (for kde, go to start button >systems> terminal)
$ type "**gksudo dolphin**" 
or type "**gksudo nautilus**"
this command brings up your default file explorer. you will be prompted for your admin password.

once password is entered the explorer windows will come up. go to /etc/default/ open file called grub. it will be automatically opened in an editor
find the line 
 GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash” 
   change it to
  
    GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash nomodeset i8042.nomux 

save the file and close
on terminal, type sudo update-grub
then reboot


now the screen brightness would be working fine
btw in mine fn+rght arrow will decrease the brightness(just the reverse)


hope this was some help
This has worked for me, and brought back the function keys as well on my toshiba.  So far this OS is my new Windows 7!  I completely removed windows 7 from this thing, and am now using open source everything, even some programs from mac.

---

### Post by Lovejoy on 2010-07-12
I had the same problem on my Acer Aspire 5741 with Ubuntu 10.04 installed. I tried this and it wouldn't even boot. It started, then went to the splash screen the colors went real funky, then nothing...

I ended up booting in safe mode and fixing the file back to the way it was originally. If anyone else tried this you may need to do the same repair I did. Here's the fix.

1) boot in safe mode, then choose continue regular boot option when it is given. (option 1)
2) you will be at a command prompt. Log in.
3) Still at the command prompt enter "sudo vi /etc/default/grub"
4) This opens vi for editing the file. Use the arrow keys to locate the cursor under the parts you added. Then press 'x' to remove the characters. (If you slip and delete what you shouldn't have, press 'i' and put it back in. Then press the esc key.)
5) After you are finished taking out the new line, press "ZZ" to save and close vi.
6) enter "sudo update-grub"
7) enter "sudo shutdown -r now" to reboot. It should be OK.

---

### Post by chandan5644690 on 2010-07-23
on my acer 4736  i have the same problem.after little bit of documentation search at the  [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)     
I added acpi_osi='Linux' in the file etc/default/grub so that the line looks like 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='Linux'"

now brightness control just works fine on both karmic and lucid 
except one thing ,it decreases the brightness when i try to increase it and increases when i try to decrease it


but after all it works fine  i can set it to maximun and have the least brightness .

---

### Post by andrei90 on 2010-08-29
> **Lovejoy said:**
> I had the same problem on my Acer Aspire 5741 with Ubuntu 10.04 installed. I tried this and it wouldn't even boot. It started, then went to the splash screen the colors went real funky, then nothing...

I ended up booting in safe mode and fixing the file back to the way it was originally. If anyone else tried this you may need to do the same repair I did. Here's the fix.

1) boot in safe mode, then choose continue regular boot option when it is given. (option 1)
2) you will be at a command prompt. Log in.
3) Still at the command prompt enter "sudo vi /etc/default/grub"
4) This opens vi for editing the file. Use the arrow keys to locate the cursor under the parts you added. Then press 'x' to remove the characters. (If you slip and delete what you shouldn't have, press 'i' and put it back in. Then press the esc key.)
5) After you are finished taking out the new line, press "ZZ" to save and close vi.
6) enter "sudo update-grub"
7) enter "sudo shutdown -r now" to reboot. It should be OK.

I have a problem with the Terminal. After I modify the "grub" and type Z two times , I get these up ( ~ ) and I cant exit the file,whats the command to save and exit the file ?

---

### Post by maberib on 2010-09-02
> **chandan5644690 said:**
> on my acer 4736  i have the same problem.after little bit of documentation search at the  [http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)     
I added acpi_osi='Linux' in the file etc/default/grub so that the line looks like 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='Linux'"

now brightness control just works fine on both karmic and lucid 
except one thing ,it decreases the brightness when i try to increase it and increases when i try to decrease it


but after all it works fine  i can set it to maximun and have the least brightness .

This solution worked for me.
 
There was one weird reboot cycle - it restarted and brought me to the normal kernel selection screen (there's windows 7 and a few other versions of Ubuntu) - then I selected the usual Ubuntu with PAE (PAE is used to recognize all of the ram installed).  The screen went totally blank, the fan spun up, then the computer shut off.  Turned it on again, selected the same Ubuntu install, and it booted up fine.  I can now adjust the brightness using the function keys.  I can't, however, adjust it using the power manager.

EDIT:
And I tried this one:     GRUB_CMDLINE_LINUX_DEFAULT=&#8220;quiet splash acpi_backlight=vendor&#8221; and the computer booted up fine, but I had no control over the screen brightness using either the hot keys or the power manager. In fact, screen brightness disappeared from the power manager as an option.

PS My screen dimming problem is happening on Ubuntu 10.04 on an Aspire 5741-5193

---

### Post by Frostshock on 2010-09-02
> **maberib said:**
> This solution worked for me.
 
There was one weird reboot cycle - it restarted and brought me to the normal kernel selection screen (there's windows 7 and a few other versions of Ubuntu) - then I selected the usual Ubuntu with PAE (PAE is used to recognize all of the ram installed).  The screen went totally blank, the fan spun up, then the computer shut off.  Turned it on again, selected the same Ubuntu install, and it booted up fine.  I can now adjust the brightness using the function keys.  I can't, however, adjust it using the power manager.

EDIT:
And I tried this one:     GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash acpi_backlight=vendor” and the computer booted up fine, but I had no control over the screen brightness using either the hot keys or the power manager. In fact, screen brightness disappeared from the power manager as an option.

PS My screen dimming problem is happening on Ubuntu 10.04 on an Aspire 5741-5193

Really, you're getting it to work on that model. That's the same model I have, although I opted for 64-bit instead of PAE, not sure if that affects resolving the screen brightness issue. I did revert GRUB settings after Ubuntu booted to a black screen, maybe I'll have to give it another try and try it two times instead.

---

### Post by nicholak on 2010-11-18
I too have put up with this issue for ages on my Aspire 5741. none of the suggestions worked, and the "vendor" grub option broke my boot also.

I did however manage to fix mine by updating the BIOS. I downloaded this from Acer for my model. there are 2 options to run it: DOS or Win, so you will need a DOS boot disk or the original OS - I kept my old HDD intact, so this was easiest for me - to swap the HD out.

Good luck!

Nicholas

---

### Post by mohxinn on 2011-02-04
Hi nicholak!

I too have Acer 5741 laptop. I have the latest BIOS installed ( v1.18 ) and yet I am unable to change brightess using Fn keys.

My laptop comes with Intel HD Graphics. I was wondering if you have the same card or do you have the Nvidia card?

Also if you have upgraded the kernel? My kernel version is 2.6.35-25. Is yours the same?

I highly appreciate the help! Thanks.

---

