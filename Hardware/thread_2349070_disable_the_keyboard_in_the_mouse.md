---
title: "disable the keyboard in the mouse"
date: 2017-01-10
forum: Hardware
---

### Post by zhangweiwu on 2017-01-10
Lenovo N700 mouse have a smart design: it has a Windows key on it. I constantly trip over it and have HUD over my face. It also randomly produce letter c, so c my ctext looks cpretty cmuch like this c cwith c all over cthe cplaces.c I believec that cthis c letter has a specific meaning to Windows but it just anoys me.

Is there a way to disable the little keyboard that comes within the mouse?

I tried to disable it in xorg.conf by this

```


Section "InputClass"
   Identifier     "Bluetooth Mouse"
   MatchIsKeyboard "on"
   MatchProduct   "Lenovo Mice N700"
   Option "Ignore" "True"
EndSection

```

But to my surprise it disabled the mouse too. So it seems to be the same Xorg device that produces both keyboard and mouse event.

---

### Post by efflandt on 2017-01-13
One way to ignore the "Windows" key on everything (including keyboard) is to install compizconfig-settings-manager package (search "compiz" in Software Center). Then when you run Compiz Config Settings Manager under "Ubuntu Unity Plugin" > Launcher tab, where is says "Key to show the Dash, Launcher and Help Overlay" click on the button that says <Super> and uncheck enabled. Or change it to a key combination that is easy to remember. That may also help if you accidentally hit the Windows key on the keyboard while gaming. Not sure if you also need to change "Key to start the Launcher Application Switcher.

I had a somewhat similar issue with a Logitech MX Master mouse which has a hidden button in the foot under your thumb that does Ctrl+Alt+Tab (which switches windows) which was sort of annoying when it would switch windows in the middle of an intense online game. In that case under the Switcher tab I changed "Key to start the Switcher for all viewports" from Ctrl+Alt+Tab to Ctrl+Alt+Home (easy enough to remember) and also Disabled whichever of the 3 buttons under that was enabled.

A more complicated way to disable that, only on the mouse, might be to look into **xinput**. You could create a file in your home dir called **.xsession** (beginning with dot) and put any xinput command(s) in that.

---

