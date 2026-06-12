---
title: "Compiz-fusion not starting properly at login"
date: 2008-10-10
forum: General Help
---

### Post by nico@nc on 2008-10-10
Hello,

I load fusion-icon at login, with Loose binding and Indirect rendering to be able to use it without problem with my nvidia Geforce Go 6400.

When I login, my screenlets looks stange, as if no compositing manager were running, and
[LIST]
[*]else every action (opening a menu, the lightning of desktop icons when the cursor is over...) is very slow, but the cursor moves normally and I've got shadows around windows, menus, etc.:
[[img]http://apu.mabul.org/up-mini/apu/2008/10/10/img-221651ragvg.jpg[/img]](http://apu.mabul.org/up/apu/2008/10/10/img-221651ragvg.jpg.html)
[*]else it looks like Metacity were running: there is no shadows nor effets when opening menus, but everything runs quickly.[/LIST]

I need to use fusion-icon "Reload window manager" option (sometimes twice) to get everything running normally.
[[img]http://apu.mabul.org/up-mini/apu/2008/10/10/img-222151b6uyl.jpg[/img]](http://apu.mabul.org/up/apu/2008/10/10/img-222151b6uyl.jpg.html)

I already tried to disable fusion-icon and set *compiz --replace --loose-binding --indirect-rendering* to be started on login, but the problem is the same. Same problem also without screenlets and/or xpad.

Thanks for your help!

---

### Post by vanadium101 on 2008-10-10
I'm having a similar problem with compiz not loading properly.
I also use fusion-icon's "Reload window manager" option to get everything running normally.

I have been running the latest compiz for a few months and i wonder if the problem is related to updates in the last few days, including ubuntu tweak

---

### Post by loomsen on 2008-10-11
If you're both on hardy, I'd recomend editing your sessions file
(should be sth like
 ~/.gnome2/sessions
It contains your startup applications, and the sequence after which they are initialized.

Try toying around a little with it, you can make some good progress I'm sure.

For Intrepid theres a new key in gconf-editor, located:
/desktop/gnome/session/required_components

replacing metacity with emerald there works fine for me ever since.

You may want to check out the two Links in my Sig as they actually deal with this, and related ptoblems.

---

### Post by nico@nc on 2008-10-11
I didn't found any sessions file in my ~/, just a .config/autostart/ folder:
```
nicolas@ubuntu-nicolas:~$ ls /home/nicolas/.config/autostart/
amsn.desktop                    gdesklets.desktop
AppMenuScreenlet.desktop        PlacesScreenlet.desktop
bluetooth-applet.desktop        qstart.desktop
ClockScreenlet.desktop          RingSensorsScreenlet.desktop
compiz.desktop                  Screenlets Daemon.desktop
DiskusageScreenlet.desktop      sodc_preload.desktop
evolution-alarm-notify.desktop  startfah.sh.desktop
fusion-icon.desktop             xpad.desktop

nicolas@ubuntu-nicolas:~$ cat /home/nicolas/.config/autostart/fusion-icon.desktop 

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=Sans nom
Name[fr_FR]=Compiz-Fusion Icon
Comment[fr_FR]=Lance et gère compiz-fusion
Comment=Lance et gère compiz-fusion
Exec=fusion-icon
X-GNOME-Autostart-enabled=true

nicolas@ubuntu-nicolas:~$ cat /home/nicolas/.config/autostart/compiz.desktop 

[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=Sans nom
Name[fr_FR]=compiz
Exec=compiz --replace --loose-binding --indirect-rendering
X-GNOME-Autostart-enabled=false
nicolas@ubuntu-nicolas:~$ 
```
:(

---

