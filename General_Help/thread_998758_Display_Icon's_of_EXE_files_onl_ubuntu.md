---
title: "Display Icon's of EXE files onl ubuntu"
date: 2008-11-30
forum: General Help
---

### Post by sudeeraj on 2008-11-30
**Open a terminal and copy and paste each command one at a time and press the enter key.**

```
sudo apt-get install icoutils
```

```
sudo gedit /usr/share/mime/packages/exemime.xml
```

**Copy and Paste the following:**
> <?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
        <mime-type type="application/x-exe">
                <comment>Windows executable</comment>
                <glob pattern="*.exe"/>
        </mime-type>
</mime-info>


**Save and Exit GEdit**

**Open a terminal and copy and paste each command one at a time and press the enter key.**

```
sudo update-mime-database /usr/share/mime/
```

```
sudo gedit /usr/bin/wineicon.sh
```

**Copy and Paste the following:**
> #!/bin/sh

f=`mktemp`

if wrestool "$1" -x -t14 > $f && [ -s $f ]; then
	id=`icotool -l $f | awk '{
		ci=int(substr($2,index($2,"=")+1));
		cw=int(substr($3,index($3,"=")+1));
		cb=int(substr($5,index($5,"=")+1));

		if (cw > w || (cw == w && cb > b)) {
			b = cb;
			w = cw;
			i = ci;
		}
		}
		END {
			print i;
		}'`

	icotool -x --index=$id $f -o "$2"
	convert -resize 48x48 "$2" "$2"		# optional
else
	cp '/usr/share/icons/crystalsvg/48x48/mimetypes/exec_wine.png' "$2"
fi

rm $f

**Save and Exit GEdit**

**Open a terminal and copy and paste each command one at a time and press the enter key.**

```
sudo chmod 755 /usr/bin/wineicon.sh
```

```
sudo gconftool --type string --set /desktop/gnome/thumbnailers/application@x-exe/command "/usr/bin/wineicon.sh %i %o"
```

```
sudo gconftool --type bool --set /desktop/gnome/thumbnailers/application@x-exe/enable true
```


**Done.** :):):):)

---

### Post by jpcote on 2008-12-08
Why is it so complicated...
Why icoutils doesn't configure itself automatically.

Maybe there is something else to just see executables files icons without having to do thoses tricks.

---

### Post by Endolith on 2008-12-14
There is already a MIME type registered for application/x-ms-dos-executable.  Modify that; don't create a redundant type for the same thing:

```
 /u/s/mime> grep -ir "\.exe" *
globs:application/x-ms-dos-executable:*.exe
globs2:50:application/x-ms-dos-executable:*.exe
packages/freedesktop.org.xml:    <glob pattern="*.exe"/>
packages/freedesktop.org.xml:      <treematch type="file" path="autorun.exe" executable="true"/>
Binary file treemagic matches

```Here is a script for superimposing the program's icon on top of the Wine icon (see attached screenshot):

[http://www.mediafire.com/?ky94kc2jdjb](http://www.mediafire.com/?ky94kc2jdjb)

You need to modify the command lines to reuse the built-in mimetype, though:

```
gconftool-2 --set /desktop/gnome/thumbnailers/application@x-ms-dos-executable/command --type string "/usr/local/bin/gnome-exe-thumbnailer %i %o"
gconftool-2 --set /desktop/gnome/thumbnailers/application@x-ms-dos-executable/enable --type boolean true
```I think it might be better to show Wine on top of the original icon, like an emblem, and use the Wine icon for every exe file even if you can't read the original icon...

A better SVG icon is in /usr/share/pixmaps/wine.svg

---

### Post by voice5sur5 on 2009-06-07
i did all what is written but nothing happened :(

---

### Post by opticyclic on 2009-08-29
I am using Linux Mint Gloria with Nautilus 2.26.2  and I can't get it to work either.
I have noticed that /usr/share/icons/crystalsvg doesn't exist on my system but I don't think that is the issue.

I am trying to run the commands individually to work out what is going on.
A variable is setup up to hold a temporary filename, then uses wrestool to extract the icon and pipe it to that temporary filename.
```
f='mktemp'

if wrestool "$1" -x -t14 > $f && [ -s $f ]; then
```
```
wrestool firefox.exe -x -t14 > /home/guest/firefox.ico
```

The output of icotool is piped though awk to determine which file (as an ico can contain several) to extract
```
id=`icotool -l $f | awk '{
ci=int(substr($2,index($2,"=")+1));
cw=int(substr($3,index($3,"=")+1));
cb=int(substr($5,index($5,"=")+1));

if (cw > w || (cw == w && cb > b)) {
b = cb;
w = cw;
i = ci;
}
}
END {
print i;
}'`
```
```
icotool -l mktemp
--icon --index=1 --width=48 --height=48 --bit-depth=4 --palette-size=16
--icon --index=2 --width=32 --height=32 --bit-depth=4 --palette-size=16
--icon --index=3 --width=16 --height=16 --bit-depth=4 --palette-size=16
--icon --index=4 --width=48 --height=48 --bit-depth=8 --palette-size=256
--icon --index=5 --width=32 --height=32 --bit-depth=8 --palette-size=256
--icon --index=6 --width=16 --height=16 --bit-depth=8 --palette-size=256
--icon --index=7 --width=256 --height=256 --bit-depth=32 --palette-size=0
--icon --index=8 --width=48 --height=48 --bit-depth=32 --palette-size=0
--icon --index=9 --width=32 --height=32 --bit-depth=32 --palette-size=0
--icon --index=10 --width=16 --height=16 --bit-depth=32 --palette-size=0

AWK Result = 7

```

Ico tool then extracts this to a png
```
icotool -x --index=$id $f -o "$2"
```
```
icotool -x --index=7 mktemp

(File mktemp_7_256x256x32.png now exists.)
```

Final step is to convert this to the correct size
```
convert -resize 48x48 "$2" "$2" # optional
```
This is where I have an issue
```
convert -resize 48x48 mktemp_7_256x256x32.png test.png
The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
bash: convert: command not found
```

However, since this line is apparently optional, I removed the line from the script, but I still don't see the icons in nautilus. :(

Any ideas?

---

### Post by sares on 2009-09-30
I got all of my exe icons look like this. Anyone know what's my problem?

---

### Post by Giblet5 on 2009-09-30
> **jpcote said:**
> Why is it so complicated...
Why icoutils doesn't configure itself automatically.

Maybe there is something else to just see executables files icons without having to do thoses tricks.

It IS complicated, but at least it can be done.

.EXE is not a standard format, even on Windows.

It would NOT be a good idea for linux (or MacOS, or Unix, or MVS) systems to attempt to interpret icon resources in .EXE files *by default*, because not all .EXE files are from Windows or DOS.

Many are from Windows' father, VMS (VMS + 1 = WNT, aka Windows NT - yeah, the same guy designed both and you thought it was new!). Attempting to treat a VMS .EXE file as having icon resources would end badly unless a lot of additional checks were performed to determine whether it's a Windows .EXE file, where the icon resources are buried, what the byte offsets are, etc.

The more ya know, the more you wanna kick your PC. Not just pretty words...

---

### Post by Endolith on 2009-09-30
> **Giblet5 said:**
> Attempting to treat a VMS .EXE file as having icon resources would end badly unless a lot of additional checks were performed to determine whether it's a Windows .EXE file, where the icon resources are buried, what the byte offsets are, etc.

Windows can obviously figure out which icon to use.  Ubuntu should do whatever they do, automatically.

---

### Post by Giblet5 on 2009-09-30
> **Endolith said:**
> Windows can obviously figure out which icon to use.  Ubuntu should do whatever they do, automatically.

No, read the post above yours. Again.

Windows *could* interpret MacOS icons correctly, but it doesn't. In fact, Windows can't interpret ANYthing that isn't Windows native.

Do you know why Windows doesn't try to interpret anything except native Windows applications?  Because there's no standard and someone will complain about the bad performance. I don't blame Microsoft for that.

---

### Post by DecryptedChaos on 2010-05-17
i relize this is for ubuntu,   but im "attempting"  to get it working under openSuSE 11.2   i followed this guide   with minor differences  e.g  without useing apt 

otherwise i followed it exactly

but it still dosen't work  anyone have any ideas

---

### Post by Akovia on 2011-03-26
I looked at this and thought I could follow the directions well enough, and it seems others did as well and had no luck. Since no one chimed in to help those, I wasn't confident I wouldn't waste a bunch of time with the same results.

For a quick and easy fix that worked like a charm for me, I just download IcoFX and installed it in Wine. It's free, polished, and the same icon editor I've used in windows for years. It's a brilliant program that does much more than extract icons. Anyway it installed w/o a hitch and I extracted my icon easily from the target exe.

Hope that may help others who are daunted with the directions above.

Ako

---

### Post by jpka on 2011-05-25
Hi!
My task is so simple, and each separate part of it is already solved and works like a charm.
But overall solution is not found by me for a years.
The task is to create shortcut (.desktop file) for my .exe files BUT with custom commandline (such a parameters pass) AND version of .exe displayed on bitmap of shortcut.
It must be done without install any additional software, because i'm pretty sure that i already have all required stuff on my system and it works.
I carefully read multiple topics but they're old and mainly talks about how to manually pull icon from .exe. It is hard and not conform with KISS rule. Currently it works automatically using gnome-exe-thumbnailer (or gnome-exe-thumbnailer.sh or so, i don't know), but the fact is exe files displayed very well and correct in Ubuntu (Nautilus). So extractor to .png is present in system. BUT, i can't find the separate png's: it only displayed but not saved :(
Other way to obtain icons is _install_ anything in wine: they put extracted icons to /home/user/.local/share/icons/.
BUT, they are not contain the version print digits, and main problem is i have _**already installed**_ .exe stuff and don't have _installer_. Wine forums says me that icon creating by wine works only during install.
At other hand, i can just create a link in my desktop, it has correct icon BUT i can't change command-line parameters for it!
So, if anyone can help me with gnome-exe-thumbnailer documentation or at least command line examples for it, i will become happy, because it looks that this software can do all i need.
Thanks!:)

---

### Post by jpka on 2011-05-25
I almost solve it.
```
sudo gedit /usr/bin/gnome-exe-thumbnailer.sh

```
and comment last line: *rm $TEMPFILE1* $TEMPFILE2 $TEMPTHUMB*
This gives me access to all icons which Nautilus shows in folder once. They located in *$TMPDIR* and are png's internally, rename it to .png if need.
Two types i find, standard png and Ubuntu Unity-style square colored background added png.
Great!
But still i lack version printing as seen in Nautilus but it is not exist in extracted png files.

---

### Post by Visbuntu718 on 2011-09-07
Hey, thanks for the walkthrough, but i have a problem. 

trevin2@TrevinsPC:~$ sudo update-mime-database /usr/share/mime/
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

trevin2@TrevinsPC:~$ 


HELP! I have GTA San Andreas and really want to see my icons!   
:confused:

---

### Post by SOS2 on 2011-11-15
[B]here is the ultimate method to having windows exe files and other format icons in file manager :
[/B]
Configure GNOME and a file browser that supports thumbnailers (such as Nautilus) to generate icons embedded inside Windows executables.

Dependencies: icoutils (can be found in most repositories).

This guide will allow your file browser (Nautilus is used in this guide, but with some amendments other browsers supporting external thumbnailers should work) to automatically extract and generate GNOME-compatible icons for Windows executables.

We'll use a combination of wrestool and icotool, provided by icoutils. First we will create a bash script to utilise these two binaries, since GNOME will only execute simple commands as thumbnailers, but not bash script or similar.

As root, create an empty file in /usr/bin named 'msiconailer' (or whatever you want to call your thumbnailer) then copy and paste this code into the contents of the file using a text editor:
```


#!/bin/bash
wrestool -x -t14 $1 | icotool -x -o $2 -

```

This code first extracts the 'main' icon (type 14) from your Windows exe (specified by the first argument $1). These binaries can include multiple cursors/icons, so we need to use wrestool to make sure we get the one we want. The data for this icon will be passed to stdout by wrestool, which we then pipe into icotool, which converts this data into a PNG format image and writes it to disk in the location specified as the second argument ($2). Here's an example use of our script:


```
msiconailer /path/to/windows.exe /path/to/exportedicon.png
```


Once you've saved the script (and don't forget to make it executable), we can configure our thumbnailer in GNOME.

The thumbnailers are configured inside gconf-editor (you can access this via the Applications menu or just enter gconf-editor into a terminal). The specific path to the thumbnailers is /desktop/gnome/thumbnailers - but to add new keys here we must use the terminal. Execute these two commands in the terminal:


```
gconftool-2 --type=bool --set "/desktop/gnome/thumbnailers/application@x-ms-dos-executable/enable" true
gconftool-2 --type=string --set "/desktop/gnome/thumbnailers/application@x-ms-dos-executable/command" "/usr/bin/msiconailer %i %o"
```


Your thumbnailer has been added - browse to a Windows executable using Nautilus to see icons generated.

If your exe icons don't appear, don't forget to empty the .thumbnails/fail folder in your home directory, and make sure things are configured correctly in Nautilus preferences (such as abandoning thumbnail-generation for files over a certain size or residing in a remote location).


**sourece** : [http://www.linuxforums.org/articles/windows-exe-icons-under-gnome_922.html](http://www.linuxforums.org/articles/windows-exe-icons-under-gnome_922.html)

---

