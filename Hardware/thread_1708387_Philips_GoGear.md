---
title: "Philips GoGear"
date: 2011-03-16
forum: Hardware
---

### Post by MattressVon on 2011-03-16
This is a tutorial for people trying to get the Philips GoGear player working on Ubuntu and all varients. It involves using Clementine and Easytag. If you install Clementine (the multi desktop port of Amoarok 1.4) and set your Phillips Go Gear player to MTP mode, it will load all your tracks on your player with the correct tags. You need to have the latest firmware upgrade, but Clementine works well with Phillips GoGear players. It uses the SQYLlite database so it plays well with GoGear players.

1.) Upgrade the firmware on your player (I did this via windows 7 on my netbook dual boot, but there are instructions around for linux). Here's their firmware page:
[http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=MP3_PLAYERS_CA&sct=FLASH_AUDIO_PLAYERS_SU&session=20070606081250_161.85.27.47&grp=PORTABLE_ENTERTAINMENT_GR&ctn=SA1110/02&mid=Link_Software&hlt=Link_Software](http://www.p4c.philips.com/cgi-bin/dcbint/cpindex.pl?slg=ENG&cat=MP3_PLAYERS_CA&sct=FLASH_AUDIO_PLAYERS_SU&session=20070606081250_161.85.27.47&grp=PORTABLE_ENTERTAINMENT_GR&ctn=SA1110/02&mid=Link_Software&hlt=Link_Software)



2.) Install Clementine:
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine

3.) Install Easytag

sudo apt-get install easytag

4.) Back up your tracks to your computer and reformat your player via the reformat menu option on the player.

5.) Point Clementine at your library:

Tools>preferences>music library

6.) Open your music in easytag and remove all comments, composer, Orig artist, copyright, url, and encoded by tags (sqylite and the gogaer firmware do not like these tag options. I'm not sure why, but this is what I had to do to get it to stop showing broken tags.)

7.) Using the Scanner in Easytag rename all tracks to this format %n - %a - %t or %n - %t. (you can do others but the dash is the important part. No dots or parenthesis. (Again not sure why, but this is what worked.)

8.) Now go into Clemementine and update your library.

9.) Set your GoGear player to MTP mode and plug it into your computer using the USB cable. 

10.) Go to Clmentine and click on devices. You should see your player. Double click on it to load it.

11.) Let Clementine scan it.

12.) Go to your library and right click on an artist or album you want to add to your player. In the pop up menu select copy to device. 

13.) Under naming options make sure the tag format matches what you set in Easytag. For example, if you did %n - %t make sure it does {%track - }%title.%extension so if you have 01 - The Grape in your folder, you get 01- The Grape in the same folder on your player.

Also at the beginning of the string you need to add the destination folder. Your string by default looks like:

%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

You want it to look like:

/music/%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

Otherwise it will just load the music onto your players root directory and not put it in the music folder.

14.) Click OK and it will load the track. Notice it only does 10 tracks at a time. I still haven't figured out how to fix this. When I do I'll post it here.

Your music should now be on your player and in the right place. Unmount your player using clementine and unplug it from the USB cable. Let it update the database and go in and check out the working tags and well sorted files!

---

### Post by MattressVon on 2011-05-20
Getting GoGear players and other players to work with Banshee and Rhythmbox is now possible too using a .is_audio_player file and the MTP protocol.

1.) Set your player to MTP mode and attach it to your computer with the included USB cable.

2.) Open the file browser and then click on the icon for your player (mine says Philips). 

3.) Once your in the window inside your player hit control h (Ctrl+H) (hold the control button and press the "H" key) to show your hidden files.

4.) Right click in the window and select the "Create Document -> Empty File" option.

5.) Name the file:   .is_audio_player

6.) Now open the file and paste the following text in it:

audio_folders=Music/,Recordings/
video_folders=Video/
output_formats=audio/flac,audio/mpeg

These are a list of directories for the programs to put your music into and a list of the file formats your player supports. I have only included flac and mp3, but you can add others by looking up the mime type syntax (ex wma = audio/x-ms-wma etc).



7.) When you're done, save your file and eject your player. :D

8.) Let your player update and then plug it back in to your computer.

9.) Open Banshee or Rythmbox and you should see your player mount. 

You can now drag and drop files on your player or in Banshee you can have the player sync with one of your playlist. I made a playlist called "GoGear" and I use that to keep my player synced up. 

Enjoy!:popcorn:

---

### Post by Toastados on 2011-06-03
This didn't work for me. I have an SA2ARA08K which mounts fine in UNR10.10 and can be seen by Rhythmbox but not Banshee. I'd prefer to use Banshee due its album art capabilities. Any ideas?

---

### Post by mike267 on 2011-12-13
I have a philips gogear ariaz 8 GB  I did exactly what MatressVon wrote but because I am a beginner couldnot go further.  I use Banshee to synchronise  before it became MTP there could be placed 250 cdtracks in 1 GB now 148 cdtracks takes 3,9 GB  it shows the albums and artists but when I push play, then he says unsupported filetype.  when I want forward,back etc. i get the same answer  Can anyone help me with this problem  I am a beginner

---

### Post by Ron W on 2011-12-18
Hello MattressVan

Can you advise on where to find firmwear upgrade for the Philips SA1943A for Ubuntu/Linux, please?

Thanks

Ron

---

### Post by paul_rubin on 2011-12-31
Thanks for posting this!  Adding the .is_audio_player file did the trick for me (GoGear Mix, Banshee, Linux Mint 11).

---

### Post by elee9900 on 2012-02-17
Worked like a charm!!! also worked for my kids Disney mp3 Player by changing 

audio_folders=Music/,Recordings/
video_folders=Video/
output_formats=audio/flac,audio/mpeg

to 

audio_folders=
video_folders=
output_formats=audio/flac,audio/mpeg

---

