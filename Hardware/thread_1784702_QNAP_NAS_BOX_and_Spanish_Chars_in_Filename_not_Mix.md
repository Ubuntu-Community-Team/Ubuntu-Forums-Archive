---
title: "QNAP NAS BOX and Spanish Chars in Filename not Mixing"
date: 2011-06-17
forum: Hardware
---

### Post by robert-drury on 2011-06-17
Dear Ubuntu team, etc. Are you sitting comfortable. GO TO PAR 3.
I am new to Ubuntu (2 months) I do like it. I have been using a NAS box for about 3 some years: QNAP TS-209 II. 2X2T HDD Raid 1 on my Netgrear giga-switch Netgrear N600 Router LAN wire around 3 bedrooms. Its ok, very much regular home network. I like my Network Cloud to be very much beside me, not some far-off what authorities are going to trawl through my personal stuff, for what reason.  NAS is meant to be a Linux based box but is not very close to Ubuntu.

NAS: never mentioned in your documentation. Supported through "FTP as admin on henry.local" [FTP protocol, Admin is me the user, Henry is the name of the box that is on the, Local network.
I do like the fact that I can put the subdirectories that I want to access onto Nutelus directory listing, which makes accessing easy. Windows solution is to allocate drive letters (A-Z) and put directory buttons on the Desktop.

I do get apparent data corruption when coping files to the NAS (mp3 etc.), and directory listing and folder accessing of the NAS. 
folder example: /Grandes Exitos/  .. access good.
files: Amiga Mia.mp3                      ... access good, Movie Player plays the music
        Coraz?-rwxrw-rw-   1 Robert   everyone 9981895 Sep  2  2010 Cuando Nadie Me Ve.mp3
  Movie Player can not play a Binary file 
       El Alma Al Aire.mp3                     ... access good, Movie Player plays the music
       La Fuerza Del Coraz?-rwxrw-rw-   1 Robert   everyone 1269505 Sep  2  2010 Lo Que Fui Es Lo Que Soy.mp3         
   Movie Player can not play a Binary file The listing continues etc. (I copy the files names here using the rename copy paste procedure) Folders with crashed names are not accessible.

I discover that Windows can handle file-names with Spanish / French character ascents any time.
Ubuntu can also handle file-names with character ascents any time BUT NOT WHEN ACCESSING THE NAS. Where the file name has a Spanish ascent character so Ubuntu replaces that character with a ? and data it pulls in from somewhere or anywhere!
I can have a trouble free life, maybe, if I use any character in a file name provided its not an assented character.  

Lastly, I notice connection to the NAS can drop after a period of time (10-15 mins) When I first access the NAS. I wait 5-6 seconds for error message and access it immediately on second attempt. Then if I do not access it again , perhaps after a long music piece there no access and must re-establish connection again.
your sincerely Robert Drury.

---

