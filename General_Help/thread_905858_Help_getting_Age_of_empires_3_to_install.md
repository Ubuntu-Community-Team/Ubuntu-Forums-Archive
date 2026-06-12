---
title: "Help getting Age of empires 3 to install"
date: 2008-08-30
forum: General Help
---

### Post by Copperteeth on 2008-08-30
Hey, I know people are always like "I cant Install game X, please help!" and they never even try looking for help but im just stumped. I have people coming over in 2 hours and they want to play Age of Empires 3, well all i have on my computer right now is ubuntu. Ive checked the wine hq page for AOE 3 but i just cant seem to get it to install for me using the guide. When i try and install it it hangs on "Preparing To install" on the Install Shield Wizard. I Tryed using Cedega but its not supported. According to the wine entry it should work but its not. I got as far as copying over the DLLs from the disc but its just hanging. Ill post the guide here:

> ** Note ** Where there is a quote, it means to type everything in between the quotes.  If there is a word enclosed in brackets, the word will be printed on a key on the keyboard.

1. Copy all .dll's from Disk1 to .wine/drive_c/windows/system32
2. Download mfc42.dll (or copy from XP) and put it in your .wine/drive_c/windows/system32 directory otherwise it will complain that the file is missing.  If you have any problems complaining about mfc42.dll, it means you have a bad copy of it.
3. Set your Windows version to Windows XP using the winecfg tool or it will complain that this game can only be installed on Windows XP
4. At a command prompt, type "mkdir ~/tempaoe3". Copy all 3 CD contents into ~/tempaoe3.
5. Change to .wine/dosdevices
6. Delete d: (At a command prompt, type "rm d:"). Type "ln -s ~/tempaoe3 d:" This will change d: to the ~/tempaoe3 directory you copied all your files to from step 4.
7. At a command prompt, type "wine cmd.exe"
8. At the DOS prompt, type "d:" and press [ENTER].
9. At the DOS prompt, Type "setup" and press [ENTER].
10. Once you see the first screen click next
11. Click I agree and move the window to the lower right corner (just leave enough of the window, to drag it back up, after the next step, you have to move it because if you don't you will not see the serial input screen and you will need to restart the installation), Then press ENTER. (You are actually pressing the NEXT button, but you can't see it)
12. Enter the serial and click next.
13. Now drag the other window back up, and Choose custom or standard installation (whichever you like and click next).
14. Now AOE3 will begin to install, and though it appears to hang, again be patient it takes about 3 minutes for the installation to react).
15. If it asks for Disk 1 again, just quit the installer.
16. Once you are done click finish, go to the console and kill the IDriver.exe and IDriverT.exe as it will have created the nescassary registry entries, but the installer will keep hanging in the memory.

Read the note below titled "MP3 sound/speeches issue workaround!" for speech issues.
	

	
 
Updated ALTERNATIVE HOWTO

1. Copy all ".dll" of disc 1 in "~/.wine/drive_c/windows/system32"
2. Download "mfc42.dll" and "d3dx9_25.dll" in "~/.wine/drive_c/windows/system32"
3. Open two Terminal windows.
4. In the first console, type "wine cmd", to start the WIne's CMD shell, also make the same to the second console.
5. In the first console, type "d:\autorun", to start the game's installation (CD1 must be inserted).
6. Follow the on-screen instructions. The installation should run normally, without delays.
7. When the installer asks for the next CD, switch to the second console and type: "eject d:". It will eject the Cd flawlessly.
8. Put in the next CD, and wait for it to mount.
9. It's better waiting about 15-20 seconds before click on "Retry" button, or the installer fails.
10. Repeat the act 7,8,9 as necessary when switch a CD.
11. Copy CD crack to Installation path 

When im running the installer in the terminal im getting the following:

```
sxgamer@sxgamer-desktop:/media/cdrom0$ wine setup.exe
err:winedevice:ServiceMain driver L"Cdr4_2K" failed to load
err:winedevice:ServiceMain driver L"Cdralw2k" failed to load
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:advapi:LookupAccountNameW (null) L"sxgamer" (nil) 0x32b16c (nil) 0x32b170 0x32b164 - stub
fixme:advapi:LookupAccountNameW (null) L"sxgamer" 0x16a348 0x32b16c 0x16a958 0x32b170 0x32b164 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\IDriver.exe" -> L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
err:rpc:I_RpcReceive we got fault packet with status 0x3e6
err:msi:ITERATE_InstallService Failed to create service L"IDriverT": 998
fixme:advapi:LookupAccountNameW (null) L"sxgamer" (nil) 0x33ceb0 (nil) 0x33ceb4 0x33cea8 - stub
fixme:advapi:LookupAccountNameW (null) L"sxgamer" 0x1b43a8 0x33ceb0 0x1aedc8 0x33ceb4 0x33cea8 - stub
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:reg:GetNativeSystemInfo (0x331554) using GetSystemInfo()
err:ntdll:RtlpWaitForCriticalSection section 0x110948 "?" wait timed out in thread 0014, blocked by 0013, retrying (60 sec)

```

Help please, i don't know where to look next. I would post this on wine hq but as i said, 2 hours they are going to be here.

---

