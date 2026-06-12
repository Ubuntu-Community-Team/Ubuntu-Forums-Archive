---
title: "Touch pad configuration how to make it permanent"
date: 2018-02-14
forum: Hardware
---

### Post by thespanishcourse on 2018-02-14
Hi,

First of all, I'm completely new to lubuntu.

I would like to disable tap on touchpad which makes writing impossible.

After browsing the forums I found that writing on LXTerminal: synclient TapButton1=0 works

However, once I switch off the computer everything reverts to the annoying tap.

Is there a way of making this permanent and not having to type synclient TapButton1=0 everytime I start the computer?

Thanks.

Regards,

Fernando.

---

### Post by vasa1 on 2018-02-14
You can put the command in your autostart. In Lubuntu 16.04, you can create/edit *$HOME/.config/openbox/autostart* to look like this:
```
(command1) &
(command2) &
(command3) &
(sleep 1s && synclient TapButton1=0) &

```"sleep" and its value is optional but the "&" at the end of each line is needed.

---

### Post by thespanishcourse on 2018-02-14
Thanks Vasa for your help 

I wasn't able to do the first step. I opened the terminal and I typed the following:

fernando@Lenovo-Yoga-300-11IBR:~$ $HOME/.config/openbox/autostart
bash: /home/fernando/.config/openbox/autostart: No existe el archivo o el directorio
fernando@Lenovo-Yoga-300-11IBR:~$ create/edit $HOME/.config/openbox/autostart
bash: create/edit: No existe el archivo o el directorio
fernando@Lenovo-Yoga-300-11IBR:~$ edit $HOME/.config/openbox/autostart
Error: no "edit" mailcap rules found for type "cannot open `/home/fernando/.config/openbox/autostart' (No such file or directory)"
fernando@Lenovo-Yoga-300-11IBR:~$ 

I'm doing something definitely wrong!!! Sorry.

Regards,

Fernando.

---

### Post by vasa1 on 2018-02-14
Sorry!

Open your file manager and press Ctrl+H to see hidden files and folders.

Look for a folder called ".config". Open it.

In there, look for a folder called "openbox". Open it.

Look for a file called "autostart". If you have such a file, open it with Leafpad which is the default text editor in Lubuntu.

Add the following text to the end of the file exactly as shown:
(sleep 1s && synclient TapButton1=0) &

Save the file. Log out, log back in. Your touchpad should be disabled automatically.

If you don't see the autostart file, right-click on a free area below the list of existing file and choose to creat a new file and call it "autostart". Then edit it as described above.

---

### Post by thespanishcourse on 2018-02-14
Thanks again vasa.

I found the folder but there were no autostart file.
There was just a file: lubuntu-rc.xml
I created autostart (No extension needed?)
I opened the file on the LeafPad
I copied and pasted (sleep 1s && synclient TapButton1=0) &
I restarted the computer but I'm still having the same problem

---

### Post by vasa1 on 2018-02-14
Just to confirm, please post the output of```
locate autostart
```and```
cat autostart
```

---

### Post by thespanishcourse on 2018-02-14
Hi Vasa,

These are the results:

fernando@Lenovo-Yoga-300-11IBR:~$ locate autostart
/etc/xdg/autostart
/etc/xdg/autostart/blueman.desktop
/etc/xdg/autostart/gnome-keyring-pkcs11.desktop
/etc/xdg/autostart/gnome-keyring-secrets.desktop
/etc/xdg/autostart/gnome-keyring-ssh.desktop
/etc/xdg/autostart/gnome-software-service.desktop
/etc/xdg/autostart/indicator-application.desktop
/etc/xdg/autostart/light-locker.desktop
/etc/xdg/autostart/lxpolkit.desktop
/etc/xdg/autostart/lxqt-compton.desktop
/etc/xdg/autostart/lxqt-desktop.desktop
/etc/xdg/autostart/lxqt-globalkeyshortcuts.desktop
/etc/xdg/autostart/lxqt-notifications.desktop
/etc/xdg/autostart/lxqt-panel.desktop
/etc/xdg/autostart/lxqt-policykit-agent.desktop
/etc/xdg/autostart/lxqt-powermanagement.desktop
/etc/xdg/autostart/lxqt-qlipper-autostart.desktop
/etc/xdg/autostart/lxqt-runner.desktop
/etc/xdg/autostart/lxqt-xscreensaver-autostart.desktop
/etc/xdg/autostart/nm-applet.desktop
/etc/xdg/autostart/org.gnome.SettingsDaemon.DiskUtilityNotify.desktop
/etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop
/etc/xdg/autostart/print-applet.desktop
/etc/xdg/autostart/pulseaudio.desktop
/etc/xdg/autostart/update-notifier.desktop
/etc/xdg/autostart/user-dirs-update-gtk.desktop
/etc/xdg/autostart/xdg-user-dirs.desktop
/etc/xdg/autostart/xfce4-power-manager.desktop
/etc/xdg/lxsession/Lubuntu/autostart
/etc/xdg/lxsession/Lubuntu-Netbook/autostart
/etc/xdg/openbox/autostart
/home/fernando/.config/autostart
/home/fernando/.config/autostart/LXinput-setup.desktop
/home/fernando/.config/lxsession/Lubuntu/autostart
/usr/bin/fcitx-autostart
/usr/bin/lxsession-xdg-autostart
/usr/lib/x86_64-linux-gnu/openbox-autostart
/usr/lib/x86_64-linux-gnu/openbox-xdg-autostart
/usr/share/fcitx/xdg/autostart
/usr/share/fcitx/xdg/autostart/fcitx-autostart.desktop
/usr/share/gdm/autostart
/usr/share/gdm/autostart/LoginWindow
/usr/share/gdm/autostart/LoginWindow/lxsession.desktop
/usr/share/indicator-application/upstart/xdg/autostart
/usr/share/indicator-application/upstart/xdg/autostart/indicator-application.desktop
/usr/share/lightdm/guest-session/skel/.config/autostart
/usr/share/lightdm/guest-session/skel/.config/autostart/guest-session-startup.desktop
/usr/share/man/man1/lxsession-xdg-autostart.1.gz
fernando@Lenovo-Yoga-300-11IBR:~$ cat autostart
cat: autostart: No existe el archivo o el directorio
fernando@Lenovo-Yoga-300-11IBR:~$ 



Thanks,

Regards,

Fernando.

---

### Post by vasa1 on 2018-02-14
You need to have ```
/home/fernando/.config/openbox/autostart
```

---

### Post by thespanishcourse on 2018-02-14
fernando@Lenovo-Yoga-300-11IBR:~$ /home/fernando/.config/openbox/autostart
bash: /home/fernando/.config/openbox/autostart: Permiso denegado
fernando@Lenovo-Yoga-300-11IBR:~$ 

It says "permission denied"

---

### Post by thespanishcourse on 2018-03-22
vasa1

Any other ideas on this issue?

Thanks.

Regards,

Fernando.

---

### Post by vanadium on 2018-03-22
The file autostart may not be present by default on lxde. It surely isn't when installing only openbox (which I tried recently for fun :-) )

Create a new file with your text editor. Add the content indicated above. Save it as .config/openbox/autostart, where .config is the hidden folder (it has a dot as the first letter in its name) in your home folder.

---

### Post by thespanishcourse on 2018-03-22
Thanks for your help vanadium.

The autostart file is here: /home/fernando/.config/openbox

The file name has no extension and it is just called autostart.

The file inside has got only one line:

(sleep 1s && synclient TapButton1=0) &

However, nothing is solved. Everytime I switch the computer off I need to open the LXTerminal and type: synclient TapButton1=0.

Regards,

Fernando.

---

### Post by vanadium on 2018-03-22
I am not quite familiar with openbox (which is used by lxde), but likely you also must set the file executable for this to work. You can do this after right-clicking the file on the permissions tab, or with the terminal: "chmod +x /home/fernando/.config/openbox".

---

### Post by thespanishcourse on 2018-03-23
Hi vanadium,

I tried both things.

1. I opened the file manager, then I located the autostart fie in /home/fernando/.config/openbox. Then I right clicked on the autostart file and I granted in properties, permissions that anyone could execute the file. However, no improvements.

2. I opened LXTerminal and I wrote [COLOR=#000000]chmod +x /home/fernando/.config/openbox.  However, nothing happened.

3. I also tried [/COLOR][COLOR=#000000]chmod +x /home/fernando/.config/openbox/autostart just in case but nothing happened either.

Thanks.

Regards,

Fernando.[/COLOR]

---

### Post by vanadium on 2018-03-25
Can you temporarily put an additional command, e.g.

```

pcmanfm &

```
That would automatically load your file manager after you login, and this would indicate whether your autostart file is correctly working.

Also try increasing the timeout, i.e. change "sleep 1s" to "sleep 2s" or longer to see if it works then.

---

### Post by thespanishcourse on 2018-04-03
It doesn't seem to work.

Un saludo,

Fernando.

---

### Post by #&amp;thj^% on 2018-04-03
> **thespanishcourse said:**
> It doesn't seem to work.

Un saludo,

Fernando.

I have found synclient commands don't seem to work in AutoStart scripts!
To enable the touchpad setting permanently , copy the 50-synaptics.conf file to /etc/X11/xorg.conf.d then edit it by adding Option "TapButton1" "0"

```
cp /usr/share/X11/xorg.conf.d/50-synaptics.conf /etc/X11/xorg.conf.d/50-synaptics.conf
```

The /etc/X11/xorg.conf.d/50-synaptics.conf should be:

```
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        Option "TapButton1" "0"
        Option "TapButton2" "3"
```
NOTE: The "TapButton2" "3" will give you two finger right click option>>if you want it, If not just don't add it.
Reboot your system

---

### Post by thespanishcourse on 2018-04-05
Thanks 1Fallen for your help.

Unfortunately, I can't access full path. I get up to /etc/X11 but there is no [COLOR=#000000]xorg.conf.d.

[/COLOR]I can't find [COLOR=#000000]50-synaptics.conf  either[/COLOR]

So, I wasn't able to edit any code.

Sorry but my knowledge is very limited.

Thanks.

Regards,

Fernando.

---

### Post by vanadium on 2018-04-06
It should work in autostart, especially if you would increase the timeout ("sleep"), such that the command is executed once the desktop is fully loaded. Your current autostart apparently is not in effect. I am not familiar with lxde. Perhaps check here on how autostart is done in lxde. There are two ways, the lxde specific way with the autostart config file, and the way as it works across a range of desktops, i.e. with .desktop text files stored in a folder under ~/.config/autostart.

If you want to try with the ".desktop" way, then you should create a desktop file containing:
```

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Adjust touchpad
Comment=A sample application
Exec=sh -c "sleep 1s && synclient TapButton1=0" &
Icon=terminal.png
Terminal=false

```

You create it with a command such as "leafpad ~/.config/autostart/touchpad.desktop". Paste in the code and save the file. Lubuntu should run any desktop file present in ~/.config/autostart/.

---

### Post by thespanishcourse on 2018-04-10
Hi Vanadium,

Yes it works!!!!!

I created the file with the command you gave me, then I pasted the code and saved the file and it is working.

Thanks for your help.

Regards,

Fernando.

---

