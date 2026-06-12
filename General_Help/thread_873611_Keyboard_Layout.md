---
title: "Keyboard Layout"
date: 2008-07-29
forum: General Help
---

### Post by sbooder on 2008-07-29
Hi All,
           I am having a problem with my keyboard layout.  For some reason it seems to be USA layout instead of UK, even though I have removed the USA layout from keyboard and UK is set to default.  It is most noticeable while emailing as the @ sign is now the " sign and the " sign is now the @ sign.

Can anyone shed some light on this please.

Thanks.

---

### Post by forger on 2008-07-29
1) What is your Ubuntu release? hardy heron 8.04.1, 8.04 or older?
2) did you log out and log in after you applied the settings in system > preferences > keyboard ?

btw, I think that the US layout is the one with @ as Shift+2 and " as Shift+'

---

### Post by sbooder on 2008-07-29
8.04 and yes I have restarted a few times.

---

### Post by RuleMaker on 2008-07-29
Try to change your layout switching keyboard shortcut or to choose other layout then the default UK, there are three variations of UK layout, try switching between them.

---

### Post by qbox on 2008-07-29
Try Reset to Default and try again from the begining.

---

### Post by sbooder on 2008-07-29
going back to default, logging off and on again then changing to UK again worked.

Thanks both.

---

### Post by sbooder on 2008-07-31
Well it worked until I rebooted, now I have to change it every time I restart. The odd thing is still that even with the USA layout removed it still defaults to US layout on every boot even though it is showing UK as default in the Layout window.

Any other thoughts out there please.

---

### Post by bsund on 2008-08-03
I have a similar problem but with different languages.

How do one change system keymap instead of just the gnome one?

Since that would probably fix the problem.

---

### Post by gomerbarkley on 2008-08-03
I have the same problem but with Dvorak layout. I had no problem with Feisty Faun, only since changing to Hardy Heron.

Every time I boot up I have to change the keyboard layout settings - add or remove a layout for it to behave (I want Dvorak as default). I've taken to adding or subtracting the Afghanistan layout (it's at the top of the list); still this requires 6+ clicks every time I start the computer - not a good long term fix.

Please help!! Thank you.

---

### Post by thegom on 2008-08-05
This has also been happening to me, since the last kernel update - I've tried changing my xorg.conf several times but it ust makes it worse. Anyone?

---

### Post by ellgor on 2008-08-05
Hi,
 Have you tried changing the Xorg configuration because that is the keymap for the comp, if you haven't then do this:

open a terminal and type in:

sudo dpkg-reconfigure xserver-xorg

Accept all the defaults until you arrive at the keyboard language select, this should be -gb- (for the UK) if it says -us- change it, accept all the defaults after this exit and reboot, hope this helps.

Regards, Ellgor.

---

### Post by sbooder on 2008-08-06
> **ellgor said:**
> 
sudo dpkg-reconfigure xserver-xorg


Regards, Ellgor.

Woops! I stupidly thought that <No> was the default and not <YES> on the first page of xserver-xorg and now when I go into Ubuntu it loads but with nothing on the desktop what so ever apart from my cube.

Is there a way I can access xserver-xorg at boot grub?

Thanks.

---

### Post by Malac on 2008-08-06
> **sbooder said:**
> Woops! I stupidly thought that <No> was the default and not <YES> on the first page of xserver-xorg and now when I go into Ubuntu it loads but with nothing on the desktop what so ever apart from my cube.
 
Is there a way I can access xserver-xorg at boot grub?
 
Thanks.
Choose Recovery Mode from the GRUB menu then Repair XServer option or Drop to Root Shell then dpkg-reconfigure xserver-xorg.
Then Reboot

---

### Post by sbooder on 2008-08-06
It won't load in recovery either. How do I drop down to Root Shell please?

My apologies, I am so new to linux, but am enjoying myself so it is OK.

---

### Post by billgoldberg on 2008-08-06
> **sbooder said:**
> It won't load in recovery either. How do I drop down to Root Shell please?

My apologies, I am so new to linux, but am enjoying myself so it is OK.

Just boot into ubuntu as normal.

Then press ctrl + alt + f2

and then you should be able to install it.

---

### Post by sbooder on 2008-08-06
I tried that but I can not see anything if I hit ctrl+alt+f2
all I can see is a white square

---

### Post by sbooder on 2008-08-06
I managed to get to the recovery and went to root shell and configured xserver, I have tired this three times using different settings and it still won't give me any furniture on the desktop when I load ubuntu (see attachment).

I am starting to think this could have nothing to do with xserver and might be a problem with the graphic drivers.

If there is a UK user out there who could let me know what the correct sequence is for going through the pages of xserver it might fix the problem.

---

### Post by Malac on 2008-08-06
> **sbooder said:**
> I managed to get to the recovery and went to root shell and configured xserver, I have tired this three times using different settings and it still won't give me any furniture on the desktop when I load ubuntu (see attachment).
 
I am starting to think this could have nothing to do with xserver and might be a problem with the graphic drivers.
 
If there is a UK user out there who could let me know what the correct sequence is for going through the pages of xserver it might fix the problem.
This could be a compiz problem by the looks of that screenshot.
Try booting to recovery again, drop to root shell, navigate to /home/**<yourusername>** then :
```
mv .compiz .compiz-old
```
then reboot see if that gets you back to the default desktop settings.

---

### Post by sbooder on 2008-08-06
Hi Malac,
          no dice I am sorry to say.  Thanks for the attempt.

Simon.

---

### Post by Malac on 2008-08-06
> **sbooder said:**
> Hi Malac,
no dice I am sorry to say. Thanks for the attempt.
 
Simon.
Okay you can name it back then.
Use same procedure except this instead ```
mv .compiz-old .compiz
```
 
Whilst in recovery mode create a new user called temp
```
useradd temp -gusers -Gadmin -ptemp
```
This will create a new user called temp with a password of temp.
 
Then try rebooting and login with this account.

---

### Post by sbooder on 2008-08-06
It created the temp user OK but it dose not let me choose because I turned off the username and password login so it just goes straight in, so it is not asking me for the temp user I have just created.  Is there code for turning login on again I can use in root shell?

Also can I remove compiz using the following in root shell?


sudo aptitude -y remove compiz-core desktop-effects
sudo aptitude -y remove compiz compiz-gnome
sudo aptitude -y remove compizconfig-settings-manager
sudo aptitude -y remove compiz-fusion-plugins-extra
sudo aptitude -y remove compiz-fusion-plugins-unofficial
sudo aptitude -y remove libcompizconfig-backend-gconf

---

### Post by Malac on 2008-08-06
> **sbooder said:**
> It created the temp user OK but it dose not let me choose because I turned off the username and password login so it just goes straight in, so it is not asking me for the temp user I have just created.  Is there code for turning login on again I can use in root shell?
sudo nano /etc/gdm/gdm.conf
scroll down and find the section beginning [daemon] #Automatic login
And set it to this:
```
[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

```Then Control O to write changes then Control X to quit.

Check that /etc/gdm/gdm.conf-custom doesn't have anything in to do with autologin too

> **sbooder said:**
> Also can I remove compiz using the following in root shell?


sudo aptitude -y remove compiz-core desktop-effects
sudo aptitude -y remove compiz compiz-gnome
sudo aptitude -y remove compizconfig-settings-manager
sudo aptitude -y remove compiz-fusion-plugins-extra
sudo aptitude -y remove compiz-fusion-plugins-unofficial
sudo aptitude -y remove libcompizconfig-backend-gconf
Hold off removing compiz for the moment.

---

### Post by sbooder on 2008-08-06
Hi Malac,
          I am in and running. It was the gdm.conf-custom that needed to be changed to let me go back to the login boxes.

But for some reason; temp would not let me in using temp as password, Anyway to cut a long story short, once I was back at the login page it also allowed me to use the options, so I changed the session to gnome failsafe. and found the problem.

For what ever reason (an update maybe), I found that my ATI Radeon was not in use in Hardware Drivers, so when I rebooted for the first time after that, I was in schtook.

Thanks for all your help and to the others whom helped too.

PS; And to top it off, my keyboard is now sorted.

Thanks again.

Simon.

---

### Post by Malac on 2008-08-06
You're Welcome :)

---

