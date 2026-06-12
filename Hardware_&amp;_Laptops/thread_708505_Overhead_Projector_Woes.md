---
title: "Overhead Projector Woes"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by rstoya05-lx on 2008-02-26
Hi,

I've got Ubuntu 7.10, T60 Thinkpad (1600x1050), Radeon x1400 graphics card. I'm using the fglrx driver,  no compiz. First let me say my setup works with 2 monitors. I've also tried it with a projector but this time I'm hard stuck and after a day of struggle I'm unable to get this to work. I had to borrow a Windows laptop to get by with my presentations. 

This is what I've tried and seen so far. 

1) With the projector connected generate xorg.confg using this command:
```
sudo aticonfig --initial=dual-head --screen-layout=above
```

Then I do Ctrl+Alt+Backspace to restart X. After logging in, I can actually see a second monitor on the projector although it looks different from the first one (doesn't have same panels, launchers, etc.). I don't know why it's different? This setup kind of works but when I try to start OpenOffice it crashes consistently. Note I can start OpenOffice on the first screen just fine.

2) With the projector connected I generate xorg.config using this command:
```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

Then I do Ctrl+Alt+Backspace and never get to the login screen. I can see the screen flashing a few times as if it's going to work but finally it gives up and puts up a basic dialog box asking me to choose a screen and graphics card. I never get farther than that. Picking ATI - Radeon (fglrx) but X still never starts successfully.

3) Given that 1 sort of worked (but without presentations) I tried using it for other stuff and noticed after a little while the projector went to sleep. It's as if it wasn't seeing the input (if that makes any sense). Re-starting X didn't help either although querying for monitors shows the projector is connected: 

```
aticonfig --query-monitor
  Connected monitors: ctr1, lvds
  Enabled monitors: crt1, lvds

```

I think something about this project is really different because it's never been this hard before (Sony XGA VPL-FX20). 

If anyone has any suggestions or insights as to what might be going it would be much appreciated. I'm no expert by any means but at this point I'm really struggling for even a basic hypothesis here, never mind things to try.

---

### Post by rstoya05-lx on 2008-02-27
Still a problem... I've tried using the xrandr command. For example:

```
xrandr --output crt1 --auto
```

But it didn't help. Does xrandr even work on ATI cards with fglrx? I wasn't able to change my resolution even for the laptop display using:

```
xrandr --output lvds --mode 1024x760
```

---

### Post by rstoya05-lx on 2008-03-06
Some more findings for those who may have the same issue...

The proprietary fglrx driver is not compatible with xrandr so you can't use that. At least not with Ubuntu 7.10.

You can use the aticonfig tool to connect to the overhead projector as follows. 

1. Make sure you're not connected to the projector

2. Boot and login 

3. Connect the overhead projector through the VGA cable

4. Type 'aticonfig --query-monitor'

5. You should see something like this:
    Connected monitors: crt1, lvds
    Enabled monitors: lvds

6. Go System > Preferences > Screen Resolution and drop to 1024 x 768
    Note: you may need to try different resolutions. It depends on the projector.

7. Type 'aticonfig --enable-monitor=crt1'
    In a few seconds you should see your output on the projector

8. Type 'aticonfig --enable-monitor=lvds' to switch back to the laptop screen

---

