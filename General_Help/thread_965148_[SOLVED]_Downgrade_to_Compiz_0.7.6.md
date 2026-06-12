---
title: "[SOLVED] Downgrade to Compiz 0.7.6?"
date: 2008-10-31
forum: General Help
---

### Post by nkri on 2008-10-31
So I installed Intrepid last night, and it seems to run alright, but Compiz is pretty sluggish and buggy.  I want to downgrade from 0.7.8 to 0.7.6, since the latter worked perfectly fine in Hardy.  I've tried Package>Force Version from Synaptic, but it's grayed out and won't work.  Any help is appreciated.

Thanks!
-nkri

---

### Post by loomsen on 2008-10-31
I'd suggest upgrading to 0.79.

```

# 		shame compiz
# 
deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

Use this to add the key:
```
wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
```

And make sure you get googles protobuf extensions _before_ you upgrade:
```

sudo apt-get libprotobuf0 libprotobuf-dev libprotobuf-java protobuf-compiler python-protobuf
```

This will boost up compiz. 1st time compiz runs it will create a folder to cache your settings (without compiz has to parse your settings-file everytime it is accessed...)

---

### Post by lavinog on 2008-10-31
Make sure it isn't your video card also.
What card do you have?
What driver are you using?
Have you tested glxgears?
Can you post output of```
glxinfo|head
```

---

### Post by nkri on 2008-10-31
I'll try upgrading later (at school right now), but in the meantime, here's the output of glxinfo|head:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group

```

I have an Intel 945GM integrated graphics controller, but I'm not sure how to find the driver.  I've tried
```
gksu displayconfig-gtk
```
to change it, but nothing happens (it worked in hardy:()

Thanks!
-nkri

---

### Post by myddewji13 on 2008-10-31
hmmm..the upgrading sounds intresting.... i might try it... just a cple qs first...
1) what plugin are u talking abt.. and how do i get it..
2)how do i undo this if it doesnt work/is more unstable/etc..?

---

### Post by loomsen on 2008-10-31
OK, step by step you'd do this:

First installing protobuf:
```

sudo apt-get libprotobuf0 libprotobuf-dev libprotobuf-java protobuf-compiler python-protobuf

```

Then add shames repo to your sources.list:
```

gksu gedit /etc/apt/sources.list

```

At the bottom of the file, append this:
```

# 		shame compiz
# 
deb http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/ ./

```

Save and close the file.

Then run this to add shames gpg key:
```

wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -

```
Simply copy and paste into a terminal.

Backup your settings if you want to. 
Open CCSM, hit preferences --> export --> chose a filename --> when prompted chose you don't want to skip default values.
This will make sure everything you configured will be written to the exported profile.


When done, run this to remove your old install:
```

sudo apt-get purge compiz

```



And then do this do get everything installed:
```

sudo apt-get update && sudo apt-get install compiz-fusion-gnome
```

OR you might as well install it through synaptic...:
```

gksu synaptic
```

Sort packages by origin, and you should see sth like this:
[[img]http://img407.imageshack.us/img407/7287/screenshot32zj0.th.png[/img]](http://img407.imageshack.us/img407/7287/screenshot32zj0.png)


*NOTES

If you don't like it, uninstall everything either with command above or through synaptic.
Then open up your sources.list again.
```

gksu gedit /etc/apt/sources.list

```

Comment out(with #) or delete what you've added before. Save, close, and install compiz from ubuntu repos again (which I don't recommend)


But usually shames repo is preferable.

---

### Post by myddewji13 on 2008-11-01
hmmm...ok so i tried it... so far this is whats happened:

the first command i pasted in but didnt work (i then changed it to sudo apt-get install ... and then it worked)

also...this command:

```
wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
```

does not get me the key...anyideas?

---

### Post by loomsen on 2008-11-01
Yup, missing an update in between editing sources.list and adding key.

So, if you added the sources, run 
```
sudo apt-get update
```

and then continue with wget...

this is what it does here:
```

docter[~] wget http://download.tuxfamily.org/shames/A42A6CF5.gpg -O- | apt-key add -
--2008-11-01 20:22:16--  http://download.tuxfamily.org/shames/A42A6CF5.gpg
Resolving download.tuxfamily.org... 212.85.158.13
Connecting to download.tuxfamily.org|212.85.158.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1690 (1.7K) [application/octet-stream]
Saving to: `STDOUT'

100%[=================================>] 1,690       --.-K/s   in 0s      

2008-11-01 20:22:16 (73.5 MB/s) - `-' saved [1690/1690]

OK
docter[~] 

```

---

### Post by myddewji13 on 2008-11-01
tried that ...this is the output i get: 

```
--2008-11-01 13:32:44--  http://download.tuxfamily.org/shames/A42A6CF5.gpg
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1690 (1.7K) [application/octet-stream]
Saving to: `STDOUT'

100%[======================================>] 1,690       --.-K/s   in 0s      

2008-11-01 13:32:51 (76.2 MB/s) - `-' saved [1690/1690]

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

```

---

### Post by myddewji13 on 2008-11-01
i also found this site:

[http://shame.tuxfamily.org/repo/?p=182](http://shame.tuxfamily.org/repo/?p=182)

noticed the repository you listed isnt exactly the same...could that be the prob?

---

### Post by myddewji13 on 2008-11-01
and i found this...same problem..i cant seem to get the key:

[http://forum.compiz-fusion.org/showthread.php?t=3657](http://forum.compiz-fusion.org/showthread.php?t=3657)

---

### Post by loomsen on 2008-11-01
Well, actually you can simply continue passing that step.

You'll be prompted that the software you're trying to install could not be authenticated and if you still want to go on. Chose yes, and it will still continue.

You'll be asked for another confirm, thats all.

---

### Post by loomsen on 2008-11-01
[Look here! Tho it's really amazing you have to do so... It seems like you have to.](http://ubuntuforums.org/showpost.php?p=6083183&postcount=11)

However, my buddy said he wasn't able neither, only when he ran sudo -i...

---

### Post by myddewji13 on 2008-11-01
ok...tried it...but it says i need emerald,...which i cannot install because there are dependencies that are uninstallable... reintalling original compiz now...thnks for the help though..

---

### Post by Cossar on 2008-11-01
Ok, I'm having the same issue. loomsen, I followed what you said, and everything worked up to where I run ```
sudo apt-get update && sudo apt-get install compiz-fusion-gnome
```

This is what I get:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-fusion-gnome: Depends: emerald (>= 0.7.7) but it is not going to be installed
                       Depends: emerald-themes (>= 0.7.7) but it is not going to be installed
                       Depends: libemeraldengine0 (>= 0.7.7) but it is not going to be installed
E: Broken packages

```

whats wrong?

---

### Post by loomsen on 2008-11-02
>  whats wrong? 

Most likely that you didn't uninstall every compiz pkg prior to installing the new repos. 

Openn up synaptic, remove everything, esp the wrapper plugin with the complete removal option.

Then, after you removed every compiz related package, run an update.

Then sort by sections, and you should be able to install everything.

Don't get stuck into metapackages. If one won't work, just ignore it.

META = [greek] above, enclosing

Metapackages actually consist only of a plain text file where dependencies are written down to. So, metapackages are just there to make life somewhat easier.
But if you've got everything installed manually, which should've worked, you may ignore metapackages...

[STEP BY STEP HOW TO GET THIS DONE](http://ubuntuforums.org/showpost.php?p=6085477&postcount=20)

---

### Post by nkri on 2008-11-03
@loomsen-thanks for the directions/tutorials...0.7.9 works great!

My only problem now is that when I use Zoom Desktop Enhanced (or plain old Zoom Desktop, for that matter), the graphics when moving the mouse while zoomed in are really choppy, while they were very smooth in 0.7.6:(

I just downloaded the 0.7.6 source code, and was wondering if there is a way to compile only the Zoom Desktop plugin instead of the entire package.  Any help is greatly appreciated:)

Thanks!
-nkri

---

### Post by loomsen on 2008-11-04
```
Any help is greatly appreciated
```

Then don't do it :) I'm using enhanced desktop zoom

Works fine for me with these values
[[img]http://img208.imageshack.us/img208/981/screenshot02iv7.th.png[/img]](http://img208.imageshack.us/img208/981/screenshot02iv7.png)

It doesn't work too well if I let compiz scale and handle the mouse tho, I guess due to the mouse being a Core pointer which, other than the  windows and your whole desktop, isn't handled by compiz...

Anyway, trial and error will do, just set it up somehow, you'll find out if you like it that way as soon as sth p***s you off actually :)

There are just too many options, impossible to have default values.

So, default is what works best for you :) Recompiling won't do the trick tho, I don't think the plugin was recently updated as it's one of the elder ones. So you'd just build the same again.

---

### Post by nkri on 2008-11-04
Alright, problem solved:)

After searching through all relevent plugins and getting nowhere, I finally found Mouse Polling Position...this is what was making the effects so bad, and moving it down to 2 got rid of the lagginess (I tried 1, but the system crashed every time and I had to do hard reboots).

Thanks for the help!
-nkri

---

### Post by mojohn on 2008-11-06
loomsen, thanks for taking time to post such detailed instructions.

I must have overlooked something because when I run "sudo apt-get install compiz-fusion-gnome" after adding shames' repo and getting the key by asking for it as root, I get an error message telling me that the package manager cannot install compiz-gnome.

I believe I've followed your instructions to the "T", including run sudo apt-get purge compiz, which reported it wasn't installed.

Any clues why I got the above error?

Thanks, mojohn

---

