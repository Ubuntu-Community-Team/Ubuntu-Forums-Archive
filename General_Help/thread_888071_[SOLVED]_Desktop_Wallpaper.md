---
title: "[SOLVED] Desktop Wallpaper"
date: 2008-08-12
forum: General Help
---

### Post by PCessna on 2008-08-12
Hey all, I was wondering if anyone knew of a script that changed the wallpaper every so many min like Macintosh

Ty
-PCessna

---

### Post by overdrank on 2008-08-12
You may look here
[http://ubuntuforums.org/showthread.php?t=880722](http://ubuntuforums.org/showthread.php?t=880722)

---

### Post by Diabolis on 2008-08-12
This will do it:
[PHP]#!/usr/bin/perl

# Folder where the images are stored
my $Folder = "~/misDocumentos/imagenes/wall/";
# List of images that will be used
my @Image = ($Folder."darkness1.jpg", $Folder."darkness2.jpg", $Folder."darkness3.jpg", $Folder."darkness4.jpg", 
$Folder."darkness5.jpg");
my $Command = "gconftool-2 -t str --set";
my $Background_Key = "/desktop/gnome/background/picture_filename";
my $Index = 0;
my $Array_Length = @Image;
my $Time = 20;  #Update 3 times per minute

while(1) {
	$Wallpaper = $Image[$Index];
	# set the background
	system("$Command $Background_Key $Wallpaper");
	$Index = ($Index + 1) % $Array_Length;
	sleep $Time;
}
done[/PHP]

1.- Copy it to a file called **changeWallpaper.pl**

2.- Make it executable
```
chmod +x changeWallpaper.pl
```

3.- Add it to your sessions
**System / Preferences / Sessions**

And it will run the next time that you log in.


You might like this too: [http://ubuntuforums.org/showthread.php?t=881100](http://ubuntuforums.org/showthread.php?t=881100)

---

### Post by karasuman on 2008-08-12
I used that script and modified it to replace your file/folder names with the ones I use.  The script is clearly doing something, but it's not finding any of the images.  It just changes my wallpaper to the default single-color (but it does this three times a minute!)

Can you tell me what I did wrong?  I've saved the pictures in home/beth/Pictures/UbuntuWallpaper/changeWallpaper, and the file names in the script are the names of the files.  :)

```
#!/usr/bin/perl

# Folder where the images are stored
my $Folder = "home/beth/Pictures/UbuntuWallpaper/changeWallpaper";
# List of images that will be used
my @Image = ($Folder."2a.jpg", $Folder."4.jpg", $Folder."68.jpg", 
$Folder."00409_osxwave_1280x800.jpg", $Folder."AquaMacfauxbythegoodness.jpg",
$Folder."arancio.jpg", $Folder."Fruity_by_saint_tpai.jpg", 
$Folder."katamarinologo.jpg", $Folder."sfondo2green.jpg",
$Folder."sour_cherry_wallpaper_2_by_monabona.jpg",
$Folder."stones.jpg", $Folder."strawberries.jpg", 
$Folder."Strawberry_Fields_Forever_by_mdvbilt.jpg", 
$Folder."Strawberry_wallpaper_by_Angelgrinder.jpg", $Folder."wall2.jpg",
$Folder."wallpaper-1280x1024-007.jpg", $Folder."Ya_Fruitcake_by_oibyrd.jpg",
$Folder."81507-thinking.jpg");
my $Command = "gconftool-2 -t str --set";
my $Background_Key = "/desktop/gnome/background/picture_filename";
my $Index = 0;
my $Array_Length = @Image;
my $Time = 20;  #Update 3 times per minute

while(1) {
    $Wallpaper = $Image[$Index];
    # set the background
    system("$Command $Background_Key $Wallpaper");
    $Index = ($Index + 1) % $Array_Length;
    sleep $Time;
}
done  
```

---

### Post by Mgiacchetti on 2008-08-12
yep its called desktop drapes

---

### Post by Diabolis on 2008-08-12
> my $Folder = "home/beth/Pictures/UbuntuWallpaper/changeWallpaper";


There is your problem. You either type it like this:
[php]my $Folder = "/home/beth/Pictures/UbuntuWallpaper/changeWallpaper";
[/php]
*notice the **/** in the beggining*

or like this:

[php]my $Folder = "~/Pictures/UbuntuWallpaper/changeWallpaper";
[/php]
*notice the **~** in the beggining, which means **home folder***

Note:
I found funny your signature haha

---

### Post by karasuman on 2008-08-12
Thanks for clarifying exactly how that works...  I actually tried all three forms (the wrong one and the two you mentioned), and nothing works.  It still persistently changes back to green, though...

---

### Post by PsychedelicWonders on 2008-08-12
hmm.  this may be something I want to do in the future, so I am gonna jump on the bandwagon now.

---

### Post by Diabolis on 2008-08-12
> my $Folder = "home/beth/Pictures/UbuntuWallpaper/changeWallpaper";

Ah! another slash missing. The one in the end.

[PHP]my $Folder = "/home/beth/Pictures/UbuntuWallpaper/changeWallpaper/";[/PHP]

---

### Post by karasuman on 2008-08-12
Still no.  :-/  For simplicity's sake, I'm cutting it down to only two pictures in the directory, which I've renamed "Ubuntu Wallpaper" because spaces are bad but something else already looks for things there and I don't think the space is causing the issue; renaming it back didn't fix it, at least.

So here's what I have that's still giving me a very persistent green screen.  (It's like I'm at war with gnome!)

```
#!/usr/bin/perl

# Folder where the images are stored
my $Folder = "home/beth/Pictures/ubuntu wallpaper/changeWallpaper/";   
# List of images that will be used
my @Image = ($Folder."2a.jpg", $Folder."4.jpg");
my $Command = "gconftool-2 -t str --set";
my $Background_Key = "/desktop/gnome/background/picture_filename";
my $Index = 0;
my $Array_Length = @Image;
my $Time = 20;  #Update 3 times per minute

while(1) {
    $Wallpaper = $Image[$Index];
    # set the background
    system("$Command $Background_Key $Wallpaper");
    $Index = ($Index + 1) % $Array_Length;
    sleep $Time;
}
done
```

---

### Post by Diabolis on 2008-08-12
[PHP]my $Folder = "/home/beth/Pictures/ubuntu\ wallpaper/changeWallpaper/";[/PHP]

- slash missing in the beginning
- the empty space needs a backslash, so it wont' break the command in two

---

