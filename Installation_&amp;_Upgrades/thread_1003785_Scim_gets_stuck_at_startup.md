---
title: "Scim gets stuck at startup"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by kennycason on 2008-12-06
Hey, 
  I'm using Ubuntu 8.10. Scim worked fine when I first installed it. however, I believe it may have been after changing something in language support it stopped working. (not sure if thats the cause or not)
but here is what it get when typing scim on the command prompt

Smart Common Input Method 1.4.7

Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.7

Starting SCIM ...


here is my scim config file:
/DefaultIMEngineFactory/en_CA = 05235cfc-43ce-490c-b1b1-c5a2185276ae
/FrontEnd/ChangeFactoryGlobally = false
/FrontEnd/IMOpenedByDefault = false
/FrontEnd/OnTheSpot = true
/FrontEnd/Socket/ConfigReadOnly = false
/FrontEnd/Socket/MaxClients = 512
/FrontEnd/X11/BrokenWchar = true
/FrontEnd/X11/Dynamic = false
/FrontEnd/X11/OnTheSpot = true
/FrontEnd/X11/ServerName = SCIM
/Hotkeys/FrontEnd/NextFactory = Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
/Hotkeys/FrontEnd/PreviousFactory = Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
/Hotkeys/FrontEnd/ShowFactoryMenu = Control+Alt+Right
/Hotkeys/FrontEnd/Trigger = Control+space,Alt+grave,Zenkaku_Hankaku,Hangul
/Hotkeys/FrontEnd/ValidKeyMask = Shift+Control+Alt+CapsLock+Meta+QuirkKanaRo
/IMEngine/Chewing/AddPhraseForward = false
/IMEngine/Chewing/ChiEngKey = Shift+Shift_L+KeyRelease
/IMEngine/Chewing/EscCleanAllBuffer = false
/IMEngine/Chewing/KeyboardType = KB_DEFAULT
/IMEngine/Chewing/SelectionKeys = 1234567890
/IMEngine/Chewing/SelectionKeysNum = 9
/IMEngine/Chewing/SpaceAsSelection = true
/IMEngine/Chewing/TriggerKey = Ctrl+space
/IMEngine/RawCode/Locales = default
/IMEngine/UIM/UUID-direct = a7260f28-f634-49b9-bda0-9563e73dfdcc
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
/Panel/Gtk/ToolBar/AlwaysShow = false
/Panel/Gtk/ToolBar/AutoSnap = true
/Panel/Gtk/ToolBar/HideTimeout = 2
/Panel/Gtk/ToolBar/POS_X = -1
/Panel/Gtk/ToolBar/POS_Y = -1
/Panel/Gtk/ToolBar/ShowFactoryIcon = true
/Panel/Gtk/ToolBar/ShowFactoryName = true
/Panel/Gtk/ToolBar/ShowHelpIcon = true
/Panel/Gtk/ToolBar/ShowMenuIcon = true
/Panel/Gtk/ToolBar/ShowSetupIcon = true
/Panel/Gtk/ToolBar/ShowStickIcon = false
/UpdateTimeStamp = 1228591470:437932

---

### Post by kennycason on 2008-12-06
I'm sorry, I just re-installed scim, restarted the computer and now it works again.

---

### Post by kennycason on 2008-12-08
Ok. nm. it happened again. this time i didn't change any language settings..
Its happened like 5 or 6 times. I've never had this happen in any other version of ubuntu.
Is there any known bug with scim as of now?

---

### Post by kennycason on 2008-12-09
Still no success.
Even after uninstalling it (sudo apt-get remove scim) then reinstalling it (sudo apt-get install scim), It still gets stuck in start up...

---

### Post by kennycason on 2008-12-12
Solved,
I just removed everything

sudo apt-get remove scim*
rm -r .scim

then instead of reinstalling scim from the command line like I usually do, I just went to System --> Management --> Language Support and re added language support for Chinese and Japanese. When I logged off and back on, it worked fine.
Thanks

---

