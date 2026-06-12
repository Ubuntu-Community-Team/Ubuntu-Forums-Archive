---
title: "Wine Doesn't Work on Some Executables?"
date: 2008-07-27
forum: General Help
---

### Post by lupinesoul on 2008-07-27
I've got an executable that Wine refuses to open.  Is there any reason it would do this?

---

### Post by VMC on 2008-07-27
> **lupinesoul said:**
> I've got an executable that Wine refuses to open.  Is there any reason it would do this?

Try running the EXE file using the Terminal and see what errors come up.
What program are you having problems with? Also how are you executing them?

---

### Post by lupinesoul on 2008-07-27
> **VMC said:**
> Try running the EXE file using the Terminal and see what errors come up.
What program are you having problems with? Also how are you executing them?
It a Pokemon MMO.  Here's the site: [http://www.pokemonworldonline.net/](http://www.pokemonworldonline.net/)

I'll try to get some errors now... That sounded weird.

---

### Post by lupinesoul on 2008-07-27
I can't get to the file... There is a whereis command, right?  How do I use it to aid in opening a program?

---

### Post by lupinesoul on 2008-07-27
> **lupinesoul said:**
> I can't get to the file... There is a whereis command, right?  How do I use it to aid in opening a program?

Never mind.  I got this message:

bash: /home/nate/Desktop/PokemonMMO/PokemonGame.exe: Permission denied

---

### Post by Green9090 on 2008-07-27
Try this:
cd /home/nate/Desktop/PokemonMMO/
sudo chmod a-x PokemonGame.exe
./PokemonGame.exe

---

### Post by lupinesoul on 2008-07-28
> **Green9090 said:**
> Try this:
cd /home/nate/Desktop/PokemonMMO/
sudo chmod a-x PokemonGame.exe
./PokemonGame.exe

Thanks, but it still says permission denied.  Is there a way to try to open it with Wine in the Terminal, or should it automatically be trying to open it with Wine?

---

### Post by dexter.deepak on 2008-07-28
you should rather try 
```
sudo chmod a+x PokemonGame.exe
```
instead of
```
sudo chmod a-x PokemonGame.exe
```
above.

---

### Post by lupinesoul on 2008-07-28
Okay, I did that.  Here's the code:

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\nate\\Desktop\\PokemonMMO\\PokemonGame.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\nate\\Desktop\\PokemonMMO\\PokemonGame.exe" failed, status c0000135

And thanks for sticking with this.

---

### Post by dexter.deepak on 2008-07-28
just right click the exe file, try running your program by "windows wine emulator"

---

### Post by lupinesoul on 2008-07-28
> **dexter.deepak said:**
> just right click the exe file, try running your program by "windows wine emulator"

I've already tried that; It doesn't work.

---

### Post by dexter.deepak on 2008-07-28
can you run any other program with wine ?

---

### Post by lupinesoul on 2008-07-28
> **dexter.deepak said:**
> can you run any other program with wine ?

Yes, ever since I got Wine, I've been able to run the Redblade D&D Character Tool.

---

### Post by eriqjaffe on 2008-07-28
> **lupinesoul said:**
> err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\nate\\Desktop\\PokemonMMO\\PokemonGame.exe") not foundSounds like you're missing some VB6 runtimes.

You should be able to install them using [winetricks](http://wiki.winehq.org/winetricks).

---

### Post by lupinesoul on 2008-07-28
I think I got winetricks installed, but the executable still doesn't open and the same error message pops up.  Is there a better Windows emulator?

---

### Post by stchman on 2008-07-28
> **lupinesoul said:**
> I think I got winetricks installed, but the executable still doesn't open and the same error message pops up.  Is there a better Windows emulator?

WINE does not run all Windows programs perfectly.  If you need to run lots of Windows programs then dual boot.  I find that I use Windows for gaming and Ubuntu for everything else.

Supposedly Cedega is a better WINE.

---

### Post by lupinesoul on 2008-07-28
> **stchman said:**
> WINE does not run all Windows programs perfectly.  If you need to run lots of Windows programs then dual boot.  I find that I use Windows for gaming and Ubuntu for everything else.

Supposedly Cedega is a better WINE.

What about those who don't have Windows, smart one?  Some people can't pay that much.

---

### Post by dexter.deepak on 2008-07-28
well , i am sorry to say , but i feel that wine cant help you run this program as it has not got those needed libraries.
maybe some other emulator can work for you; here's what i can offer:
[http://www.linuxbasis.com/downemu.html](http://www.linuxbasis.com/downemu.html)

i have heard a lot bout cadega...but even i cant afford it, its not open:)

---

### Post by dexter.deepak on 2008-07-29
just got to know that dlls can be installed for wine also.
i had a simple google search for your dll and got this :
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)

just put this dll (i think it will be in .zip format , so you'll have to extract it first) in ~/.wine/drive_c/windows/system/

---

### Post by dexter.deepak on 2008-07-31
@OP
can you please reply if the above stuff worked for you. i am keen to know it as i have yet not tested such stuff.

---

