---
title: "[SOLVED] I think I just broke Wine, plz help"
date: 2008-11-13
forum: General Help
---

### Post by memorex11218 on 2008-11-13
I think I just broke Wine. I was using it to try to install Microsoft Office 07 (need it for school, OpenOffice doesn't cut it). The website I was going off is [http://sudosys.be/?q=office2007_wine](http://sudosys.be/?q=office2007_wine) , I was using wine 1.0.1 (skipped the first step) I got up to the adding the rpcrt4.dll, making the long story short, MS office 2007 didn't work for me. Now Wine doen't work. I can click on various files and it doesn't do anything. I have tried reinstalling and completely removing it. When I run winecfg I get this:

err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

I'm pretty new to using Ubuntu, somebody please help.

---

### Post by CatKiller on 2008-11-14
If you delete the ~/.wine folder, your Wine environment should be back to its original state.

---

### Post by memorex11218 on 2008-11-14
ok, i just replaced the rpcrt4.dll with a copy from my windows installation. Now Wine runs but extremely slow (I click on something and it takes 2 min to open it) Does anyone know how to get it to run like it used to?

---

### Post by memorex11218 on 2008-11-14
Um, where is the ~/.wine folder?

---

### Post by Carl Hamlin on 2008-11-14
> **memorex11218 said:**
> I think I just broke Wine.

Unless your machine is ancient or you don't actually *have* a copy of Windows lying about, I'd highly recommend running Windows in VirtualBox over running Windows programs in Wine.

So far as speeding Wine up goes, I'd start looking in the configuration to see what's different between now and before.

---

### Post by Carl Hamlin on 2008-11-14
> **memorex11218 said:**
> Um, where is the ~/.wine folder?

~ is a mnemonic for your home directory.

---

### Post by memorex11218 on 2008-11-14
Sry guys but I cant seem to find the wine folder you are talking about. Wine tries to run but doesn't (programs start but no result of install) work properly.

---

### Post by CatKiller on 2008-11-14
> **memorex11218 said:**
> Um, where is the ~/.wine folder?

~ means /home/<*username*> (your Home folder). Files and directories that start with a . are hidden by default. Ctrl-H will toggle whether these files are displayed or not.

How did you replace the .dll file with your Windows one if you couldn't find the folder to put it in?

---

### Post by memorex11218 on 2008-11-14
Ok, I think that fixed it. MS Office 2003 installed fine and everything runs except excel (crashes on both normal and safe mode). oh, and i replaced it into the folder that wine made on the C:\ drive like it said on the website.

---

### Post by Carl Hamlin on 2008-11-14
> **memorex11218 said:**
> Ok, I think that fixed it.

Rock on.

There's a *lot* of data that gets stored in hidden directories in your home directory. If you're of the inclination, I'd suggest taking some time to familiarize yourself with what goes where - that's information that can come in *extremely* handy in a pinch, and it's fun stuff to know.

---

