---
title: "i can't switch on/off mode with SCIM on 8.10"
date: 2008-11-02
forum: General Help
---

### Post by dungpt on 2008-11-02
i'm using Ubuntu 8.10 and i can't switch on/off mode with SCIM
with any shortcut :confused: ??!

---

### Post by kfir_w on 2008-11-02
I can't even turn it off. When choosing exit, it just runs it again.
Killing the "scim-bridge" process seems to be the only way to turn it off.
And another thing - even worse - the "auto combine phrase" option for entering chinese pinyin doesn't work even if selected.
Seems like this new version is bugged, No?

---

### Post by mdurham on 2008-11-03
> Seems like this new version is bugged, No?
No, it works 100% here.

---

### Post by Interpreter on 2008-11-03
cant kill it either, its annoying as hell, im sitting here shouting die you **** die ....it just keeps coming back like a frigging zombie im am so close to an awkward SLAM DA KEYBOARD situation.
Some one please find a way too KILL it.

WUAH

die you "smart" piece of crippleware, I didnt even start that program in the first place btw.

---

### Post by kfir_w on 2008-11-03
Hi,
What version of SCIM are you using? 1.4.6? Is it under Gnome or KDE?
Could you attach your .scim/config file?

Thanks

---

### Post by mdurham on 2008-11-03
> **kfir_w said:**
> Hi,
What version of SCIM are you using? 1.4.6? Is it under Gnome or KDE?
Could you attach your .scim/config file?

Thanks

Who are you addressing those questions to?

---

### Post by Interpreter on 2008-11-03
As for me that would be
```
/FrontEnd/ChangeFactoryGlobally = false
/FrontEnd/IMOpenedByDefault = false
/FrontEnd/OnTheSpot = true
/FrontEnd/SharedInputMethod = true
/FrontEnd/Socket/ConfigReadOnly = false
/FrontEnd/Socket/MaxClients = 512
/FrontEnd/X11/BrokenWchar = true
/FrontEnd/X11/Dynamic = false
/FrontEnd/X11/OnTheSpot = true
/FrontEnd/X11/ServerName = SCIM
/Hotkeys/FrontEnd/NextFactory = Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
/Hotkeys/FrontEnd/Off =
/Hotkeys/FrontEnd/On =
/Hotkeys/FrontEnd/PreviousFactory = Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
/Hotkeys/FrontEnd/ShowFactoryMenu = Control+Alt+Right
/Hotkeys/FrontEnd/Trigger = Control+space,Alt+grave,Zenkaku_Hankaku,Hangul
/Hotkeys/FrontEnd/ValidKeyMask = Shift+Control+Alt+CapsLock+Meta+QuirkKanaRo
/IMEngine/RawCode/Locales = default
/Panel/Gtk/Color/ActiveBackground = light sky blue
/Panel/Gtk/Color/ActiveText = black
/Panel/Gtk/Color/NormalBackground = #F7F3F7
/Panel/Gtk/Color/NormalText = black
/Panel/Gtk/DefaultSticked = false
/Panel/Gtk/Font = default
/Panel/Gtk/LookupTableEmbedded = true
/Panel/Gtk/LookupTableVertical = false
/Panel/Gtk/ShowStatusBox = false
/Panel/Gtk/ShowTrayIcon = true
/Panel/Gtk/ToolBar/AlwaysHidden = false
/Panel/Gtk/ToolBar/AlwaysShow = false
/Panel/Gtk/ToolBar/AutoSnap = true
/Panel/Gtk/ToolBar/HideTimeout = 2
/Panel/Gtk/ToolBar/POS_X = -1
/Panel/Gtk/ToolBar/POS_Y = -1
/Panel/Gtk/ToolBar/ShowFactoryIcon = true

```

I played with the language support for a bit. And it's there ever since.
Intrepid seems to be bilingual, and while I'm fine with English, I'd rather have my system use but one language. That being Krauttalk.
For some reason it gave me old dialogboxes in English, and I don't think it's that poorly translated. Is this process of fiddling with the language settings supposed to call a damn application which just won't die? Weird. Usability = fail.

---

### Post by Interpreter on 2008-11-04
I ended up just "sudo apt-get remove scim" -ing it, for it was sucking the will to live out of me.

---

### Post by nidelius on 2008-11-06
Works like a charm for me I even got a "fast switch" icon working at the bottom right

Take a look here
[http://www.nidelius.com/wiki/index.php/Korean_in_Ubuntu](http://www.nidelius.com/wiki/index.php/Korean_in_Ubuntu)
[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

> open a terminal 
sudo apt-get install im-switch 
sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-hangul scim-tables-ko
sudo touch /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup

Restart X (CTRL+ALT+Backspace) 

sudo apt-get install uim-hangul 

Restart X (CTRL+ALT+Backspace) 

Now edit your right klick the little type writer in the top of the screen and choose SCIM setup
Under IMEngine > Global Setup
set your shortcut under the prefered language. Don't forget to set one on Korean and one on your default language if you want to be able to switch back fast

now press apply and ok 

if needed exit SCIM and
(alt+F2) then type scim 

Now it should work perfectly!

---

