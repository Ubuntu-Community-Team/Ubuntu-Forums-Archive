---
title: "Kate editor spamming terminal"
date: 2008-11-11
forum: General Help
---

### Post by Leperous on 2008-11-11
Hi,

Apologies if this is the wrong place to be posting this, but I couldn't find anywhere more relevant or helpful ;)

I do a lot of coding using the Kate editor. It's always output some amount of garbage to the terminal; opening it up in 7.x (or opening up another KDE app such as KDVI in 8.10) throws up
> QSettings::sync: filename is null/empty
kbuildsycoca running...
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QApplication::notify: Unexpected null receiver
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty
QSettings::sync: filename is null/empty


However since upgrading to 8.10 it's gone beserk. Merely opening Kate throws up the following warnings/errors, which I've tried Googling but to no avail; the program itself seems to run just fine though. Is there a way to suppress these? Why is it seemingly only me getting these errors? Thanks for any help.

> $ kate
kate(9651): createDoc
kate(9651) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/home/ollie/.kde/share/apps/kate/sessions"
kate(9651) KateApp::initKate: Setting KATE_PID: ' 9651 '
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "Default Session"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/Default Session.katesession"  dir[i]; "Default Session.katesession"
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "magcode"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/magcode.katesession"  dir[i]; "magcode.katesession"
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "Thesis"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/Thesis.katesession"  dir[i]; "Thesis.katesession"
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "Default Session"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/Default Session.katesession"  dir[i]; "Default Session.katesession"
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "magcode"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/magcode.katesession"  dir[i]; "magcode.katesession"
kate(9651) KateSessionManager::updateSessionList: FOUND SESSION:  "Thesis"  FILE:  "/home/ollie/.kde/share/apps/kate/sessions/Thesis.katesession"  dir[i]; "Thesis.katesession"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "mod_bfield.f90"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "mod_derivatives.f90"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
kate(9651) KMimeTypeFactory::parseMagic: Now parsing  "/usr/local/share/mime/magic"
kate(9651) KMimeTypeFactory::parseMagic: Now parsing  "/home/ollie/.local/share/mime/magic"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "input.par"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "mod_evolutions.f90"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "mod_initial_data.f90"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "mod_input.f90"
kate(9651): createDoc
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"
kate(9651) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "main.f90"
kate(9651) KateViewDocumentProxyModel::updateBackgrounds: false
kate(9651) KateMainWindow::KateMainWindow: **************************************************************************** 0x958cec8
kate(9651) KateViewDocumentProxyModel::updateBackgrounds: false
kate(9651) KateViewDocumentProxyModel::updateBackgrounds: false
kate(9651) KateApp::startupKate: KateApplication::init finished successful
kdeinit4: preparing to launch 
kate(9651) KateViewDocumentProxyModel::updateBackgrounds: true

---

### Post by justleen on 2008-11-11
your starting it from a terminal, thus all output goes to the terminal window...perfectly normal

Try starting it from the menu. Or, start with ```
kate &
```
the & will place the proccess in the background. pressing enter will give you a prompt back (and should stop the output)

or ```
 kate > /dev/null 2>&1 
```
that will redirect any output to dev null

---

### Post by Leperous on 2008-11-11
Yes, I know the output goes to the terminal :) Using ampersand doesn't remove the messages, though.

I was hoping for some KDE setting or *something* more permanent but I like the sending-to-null idea, thanks.

---

### Post by justleen on 2008-11-11
well... you can always use the nohup option.. that will detach the proccess from the current shell, and place it in the background (so you can kill your terminal, and kate will not close)
```
 nohup kate 
```

---

