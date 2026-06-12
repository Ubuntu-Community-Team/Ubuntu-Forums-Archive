---
title: "Text reader for linux"
date: 2008-09-12
forum: General Help
---

### Post by Alien260 on 2008-09-12
Hello, 

I just wanted to know if anyone knows if there is anything like a text reader for linux?

I used this [LINK]("http://www.readwritegold.com/") for windows before but it worked well. 

Thanks
Alien

---

### Post by SunnyRabbiera on 2008-09-12
There is festival, I think its in the repos

---

### Post by Predator106 on 2008-09-12
Oh like Text-to-Speech, yeah, I've heard festival is the best, like the above said, it should be in the package manager.

---

### Post by Alien260 on 2008-09-12
> **Predator106 said:**
> Oh like Text-to-Speech, yeah, I've heard festival is the best, like the above said, it should be in the package manager.

Ok, i downloaded it, 

But im not to sure how to use it? Dose it actually have an interface? if i run it through terminal i get some random option to run a string. But when i do it gives an error?!

Isnt there a way to open the UI if it has one?

Thanks 
[COLOR="Lime"]Alien [/COLOR]

---

### Post by tlacuache on 2008-09-12
Festival is great, although the default voice leaves something to be desired, in my opinion. I followed [this tutorial ]("http://ubuntuforums.org/showthread.php?t=751169")to find a better-sounding voice (nitech_us_slt_arctic_hts was my favorite).

As for a GUI, festival itself does not have a GUI, but I wrote a couple of simple nautilus scripts that I use to read text files.

These go in ~/.gnome2/nautilus-scripts:

Save the following file as "Read" in the aforementioned directory:
```

#!/usr/bin/perl -w

use strict;

my @files = split("\n", $ENV{NAUTILUS_SCRIPT_SELECTED_FILE_PATHS});
foreach my $file (@files)
{
  if ( -e $file )
  {
    `festival --tts '$file'`;
  }
}

```

If you have lame installed, you can have this script create MP3s from your text files. I called this one ReadToMP3:
```

#!/usr/bin/perl -w

use strict;

my @files = split("\n", $ENV{NAUTILUS_SCRIPT_SELECTED_FILE_PATHS});
foreach my $file (@files)
{
  if ( -e $file )
  {
    my $wavName = $file.".tmp.wav";
    my $mp3Name = $file.".mp3";

    `cat '$file' | text2wave -o '$wavName'`;

    if ( -e $wavName) {
      `lame '$wavName' '$mp3Name'`;
      unlink($wavName);
      if (-e $mp3Name) {
        `zenity --info --text="Converted $file to $mp3Name"`;
      } else {
        `zenity --info --text="Failed to convert $file to $mp3Name"`;
      }
    } else {
      `zenity --info --text="Failed to convert $file to $wavName"`;
    }
  } else {
      `zenity --info --text="$file could not be opened"`;
  }
}

```

Like I said, after you've installed festival and lame just save those files in your .gnome2/nautilus-scripts directory. Now you can right-click on text files and choose the appropriate script from the "Scripts" submenu to have them read to you.

Good luck.

---

