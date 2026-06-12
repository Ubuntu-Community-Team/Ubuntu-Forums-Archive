---
title: "set keybindings in kubuntu 4"
date: 2008-08-31
forum: General Help
---

### Post by agim on 2008-08-31
I would like to set certain keybindings in kubuntu 8.04.
For instance, I would like to be able to launch konsole, basket, and a couple of other often used programs with a hotkey.

If anyone can point me in the right direction I would appreciate it.

Thanks

---

### Post by arch0njw on 2008-09-01
You are *supposed* to be able to edit the menu with the menu editor.  /usr/lib/kde4/bin/kmenuedit.  I think this was released as part of 4.1, and is not in 4.0.

*However*, I have edited my menu a number of times, specifying shortcut keys, and none of my keybindings seem to work.  I suspect an issue with in in KDE4.  I need to test on another machine, confirm, and then I'm going to file a bug.

If you are able to confirm this, let me know.  I'd like to accumulate as much data for the bug as possible.

---

### Post by arch0njw on 2008-09-01
Yeah, I confirmed this on another machine.

```
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{b4271e99-0000-4000-8966-5158550e7d48}"  -  "Activate KSIRC Window" : QKeySequence("Ctrl+Alt+I")                                                     
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{b4271e99-0000-4000-8966-5158550e7d48}"  -  "Activate KSIRC Window" : QKeySequence("") QKeySequence("")                                                       
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{6cff0e0b-0000-4000-a50c-404242a3e5e8}"  -  "Type 'Hello'" : QKeySequence("Ctrl+Alt+H")                                                                                
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{6cff0e0b-0000-4000-a50c-404242a3e5e8}"  -  "Type 'Hello'" : QKeySequence("") QKeySequence("")                                                                
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{3e72cad5-0000-4000-bc46-32c1e4b4e5bf}"  -  "Run Konsole" : QKeySequence("Ctrl+Alt+T")                                                                                 
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{3e72cad5-0000-4000-bc46-32c1e4b4e5bf}"  -  "Run Konsole" : QKeySequence("") QKeySequence("")                                                                 
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{0c20a735-0000-4000-ae13-9f01c74a2020}"  -  "Remap Ctrl+W to Ctrl+F4 in Qt Designer" : QKeySequence("Ctrl+W")                                                          
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{0c20a735-0000-4000-ae13-9f01c74a2020}"  -  "Remap Ctrl+W to Ctrl+F4 in Qt Designer" : QKeySequence("") QKeySequence("")                                      
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{e4ff2886-0000-4000-b99a-ace736104d42}"  -  "Perform D-Bus call 'kdesktop KDesktopIface popupExecuteCommand()'" : QKeySequence("Ctrl+Alt+W")                           
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{e4ff2886-0000-4000-b99a-ace736104d42}"  -  "Perform D-Bus call 'kdesktop KDesktopIface popupExecuteCommand()'" : QKeySequence("") QKeySequence("")           
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{abdf09bf-0000-4000-b441-5237b66e7aac}"  -  "Next in XMMS" : QKeySequence("Ctrl+Alt+B")                                                                                
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{abdf09bf-0000-4000-b441-5237b66e7aac}"  -  "Next in XMMS" : QKeySequence("") QKeySequence("")                                                                
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{3f6d29f2-0000-4000-958a-7a3c886cdf9a}"  -  "Go to KDE Website" : QKeySequence("E")                                                                                    
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action                                   
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{3f6d29f2-0000-4000-958a-7a3c886cdf9a}"  -  "Go to KDE Website" : QKeySequence("") QKeySequence("")                                                           
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{21f49ecd-0000-4000-ac39-65f22bcf2d67}"  -  "PrintScreen" : QKeySequence("Print")
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{21f49ecd-0000-4000-ac39-65f22bcf2d67}"  -  "PrintScreen" : QKeySequence("") QKeySequence("")
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{494ca6a7-0000-4000-a6c6-e888cc131167}"  -  "K Menu - kde4-konsole.desktop" : QKeySequence("Ctrl+Shift+!")
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{494ca6a7-0000-4000-a6c6-e888cc131167}"  -  "K Menu - kde4-konsole.desktop" : QKeySequence("Ctrl+Shift+!") QKeySequence("")
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{494ca6a7-0000-4000-a6c6-e888cc131167}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{86c42d27-0000-4000-aaff-c6b5e4879799}"  -  "K Menu - kde4-konsole.desktop" : QKeySequence("Ctrl+Shift+~")
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Making it a configuration action
kmenuedit(6379) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{86c42d27-0000-4000-aaff-c6b5e4879799}"  -  "K Menu - kde4-konsole.desktop" : QKeySequence("") QKeySequence("")
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{b4271e99-0000-4000-8966-5158550e7d48}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{6cff0e0b-0000-4000-a50c-404242a3e5e8}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{3e72cad5-0000-4000-bc46-32c1e4b4e5bf}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{0c20a735-0000-4000-ae13-9f01c74a2020}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{e4ff2886-0000-4000-b99a-ace736104d42}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{abdf09bf-0000-4000-b441-5237b66e7aac}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{3f6d29f2-0000-4000-958a-7a3c886cdf9a}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{21f49ecd-0000-4000-ac39-65f22bcf2d67}"
kmenuedit(6379) KHotKeys::ShortcutsHandler::removeAction: Removing action for  "{86c42d27-0000-4000-aaff-c6b5e4879799}"
QDBusConnection received a message of type 3 that it shouldn't have
error: "org.freedesktop.DBus.Error.UnknownObject" "No such object path '/modules/KHotKeys'"

```

---

### Post by arch0njw on 2008-09-01
Bug has been filed:

[http://bugs.kde.org/show_bug.cgi?id=170222](http://bugs.kde.org/show_bug.cgi?id=170222)

---

