---
title: "Access Windows Registry through Linux"
date: 2008-07-30
forum: General Help
---

### Post by Ryuji5864 on 2008-07-30
Does anyone know how to access and modify the windows registry through linux?

---

### Post by pauper on 2008-07-30
If you have wine installed...

```
regedit
```

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> If you have wine installed...

```
regedit
```

Thanks for answering my first question. 

I am trying to change the windows desktop background through the registry using linux. I know where the files are in the registry [HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Desktop\General\Wallpaper and HKEY_CURRENT_USER\Control Panel\Desktop]

Do you think I should change both of these registry files, or only one?

On another note, can you specify which user? >.>

---

### Post by pauper on 2008-07-30
Have no idea regarding registry. Just tested another approach--works:

```
echo "[Desktop]
Wallpaper=c:\windows\image_name.bmp" >> ~/.wine/drive_c/windows/win.ini
wineboot
winecfg
```

"Graphics" tab, check box "Emulate a virtual desktop". OK.

[edit:]
Make sure image_name.bmp is actually *.bmp--not *.jpg or *.png, and that
you put it in ~/.wine/drive_c/windows directory.
Note: Use GIMP to convert image: just choose save a copy of any current
image and append .bmp at the end of filename.

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> Have no idea regarding regestry. Just tested another approach--works:

```
echo "[Desktop]
Wallpaper=c:\windows\image_name.bmp" >> ~/.wine/drive_c/windows/win.ini
wineboot
winecfg
```

"Graphics" tab, check box emulate a virtual desktop. OK.
Using your method can you specify which user? such as guest4

---

### Post by pauper on 2008-07-30
Well, if you log in as guest4 and make all changes, it will be persistent for
guest4 only. There could be more elegant way via registry, but I very seldom
run wine, so I'm not good here.

---

### Post by jimv on 2008-07-30
> **pauper said:**
> Well, if you log in as guest4 and make all changes, it will be persistent for
guest4 only. There could be more elegant way via registry, but I very seldom
run wine, so I'm not good here.

I don't think he's talking about WINE.  If I'm not mistaken, Ryuji5864 is trying to modify the registry of Windows installed on another partition.

I'm just curious, Ryuji5864, why are you trying to do it from Linux?

---

### Post by Ryuji5864 on 2008-07-30
> **jimv said:**
> I don't think he's talking about WINE.  If I'm not mistaken, Ryuji5864 is trying to modify the registry of Windows installed on another partition.

I'm just curious, Ryuji5864, why are you trying to do it from Linux?

You are extremely close to what I am trying to accomplish in Linux. I am trying to access and modify the windows desktop background registry file through Linux. I am trying to change the desktop background for a user with limited rights. Keep in mind I am doing this with a Ubuntu Live CD. 

The reason why I am doing this in linux. 
1) The university which I go to school disabled the rights for limited users to change the windows desktop background.
2) Because there is always a way!

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> Well, if you log in as guest4 and make all changes, it will be persistent for
guest4 only. There could be more elegant way via registry, but I very seldom
run wine, so I'm not good here.

What if in windows, the guest4 is a limited user and the rights to change the background are disabled for this user, will this effect you method for changing the desktop background through linux?

---

### Post by pauper on 2008-07-30
Who are you trying to impress there? :)

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> Who are you trying to impress there? :)

Actually, I am not trying to impress anyone. I am just sick and tired of the damn desktop background advertisements. I am about to test your method >.>

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> 
```
echo "[Desktop]
Wallpaper=c:\windows\image_name.bmp" >> ~/.wine/drive_c/windows/win.ini
wineboot
winecfg
```

"Graphics" tab, check box "Emulate a virtual desktop". OK.

[edit:]
Make sure image_name.bmp is actually *.bmp--not *.jpg or *.png, and that
you put it in ~/.wine/drive_c/windows directory.
Note: Use GIMP to convert image: just choose save a copy of any current
image and append .bmp at the end of filename.
I am having problems with this method. I am trying to do this off of the live CD. ~/.wine/drive_c/windows/win.ini  Couldn't find.

---

### Post by Separ on 2008-07-30
Are you trying to change the actual Windows registry? Because I think everyone here is assuming you are trying to edit the Wine registry. Unless I'm mistaken and the wine one can edit the registry of a windows machine? :o

---

### Post by Ryuji5864 on 2008-07-30
Editing the registry keys using wine works, but it does not show the registry keys to change the background. HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Desktop\General\Wallpaper and HKEY_CURRENT_USER\Control Panel\Desktop do not show up using regedit in linux. So, I cannot change the desktop background using regedit.

There is bound to be a way to change the desktop background for a limited user in linux. Any ideas?

---

### Post by Ryuji5864 on 2008-07-30
> **Separ said:**
> Are you trying to change the actual Windows registry? Because I think everyone here is assuming you are trying to edit the Wine registry. Unless I'm mistaken and the wine one can edit the registry of a windows machine? :o

I am trying to edit the Windows registry.

---

### Post by pauper on 2008-07-30
If you have physical access to the computer, I don't see what kind of
difference Live CD makes: you either need admin's password or some relevant
permissions to modify forced background behavior inside Windows.

My apologies for misleading information.

---

### Post by Ryuji5864 on 2008-07-30
> **pauper said:**
> If you have physical access to the computer, I don't see what kind of
difference Live CD makes: you either need admin's password or some relevant
permissions to modify forced background behavior inside Windows.

My apologies for misleading information.

I am a limited user in windows. I have tried several different methods to change the desktop background. Registry, gpedit.msc, applying a background from a webpage and no luck.

You do not know of any other methods to change the background through linux?

---

### Post by mrboojive on 2008-07-30
Where is the file that Windows is setting as the background? Maybe you can use the live cd to overwrite that file with whatever you want.

---

### Post by Ryuji5864 on 2008-07-30
> **mrboojive said:**
> Where is the file that Windows is setting as the background? Maybe you can use the live cd to overwrite that file with whatever you want.

Currently I am searching for the file in windows. I am not able to access regedit, or gpedit.msc. The most I can do currently is click apply on a background and it changes the background ONLY when I lock the PC.

---

### Post by estyles on 2008-07-30
Yeah, using wine isn't going to help, AFAICT, because it keeps its own versions of windows system files in /.wine - it doesn't let you modify the registry of a Windows installation on another partition.  Unless I'm way off base...  :confused:

I think what you are looking for is the name of the file location that the registry is stored in.  Assuming it's an NT-based version, your user's HKEY_CURRENT_USER hive is stored in %USERPROFILE%\ntuser.dat.  Where %USERPROFILE% usually expands to C:\Documents and Settings\username.

As for the format of that file, I have no idea.  I can think of two options that might work.  Search somewhere for an open-source registry editor, if such a thing exists, and modify that ntuser.dat file.  Or see if you can edit that file using the regedit program included in wine.  Perhaps use regedit, Import..., then make your changes, then Export... and overwrite the file on the local system.

As I type this, I realize that there are some nefarious things you can do if you get it to work, and I'm thinking maybe I shouldn't help you to bring down the local computer lab...  At any rate, that's all I know, so you'd have to do some searching for any more info.

---

### Post by Ryuji5864 on 2008-07-30
> **estyles said:**
> Yeah, using wine isn't going to help, AFAICT, because it keeps its own versions of windows system files in /.wine - it doesn't let you modify the registry of a Windows installation on another partition.  Unless I'm way off base...  :confused:

I think what you are looking for is the name of the file location that the registry is stored in.  Assuming it's an NT-based version, your user's HKEY_CURRENT_USER hive is stored in %USERPROFILE%\ntuser.dat.  Where %USERPROFILE% usually expands to C:\Documents and Settings\username.

As for the format of that file, I have no idea.  I can think of two options that might work.  Search somewhere for an open-source registry editor, if such a thing exists, and modify that ntuser.dat file.  Or see if you can edit that file using the regedit program included in wine.  Perhaps use regedit, Import..., then make your changes, then Export... and overwrite the file on the local system.

As I type this, I realize that there are some nefarious things you can do if you get it to work, and I'm thinking maybe I shouldn't help you to bring down the local computer lab...  At any rate, that's all I know, so you'd have to do some searching for any more info.

Thanks for all of your information. I will definitely look into trying your idea.

As for bringing down the local computer lab. I do not want to be kicked out of college, or something of that nature. I plan on continuing my studies in computer science. My only plan is to change the desktop background through windows using linux. >.>

---

