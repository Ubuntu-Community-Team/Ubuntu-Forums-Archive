---
title: "Vusys I-DJ 670 hdd mp3-player with Ubuntu"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by Zibri on 2007-06-11
Hello!

Bought a pretty cheap hdd mp3-player, a Vusys I-DJ 670. The problem is that the sorting features is based on some weird database or something, that relies on a windows program. I don't know if there is some way to make Amarok do the same, or something... Tried to google but no good :(

---

### Post by tamias on 2007-11-27
*bump* I'd be interested in a solution to this, too.

At the moment I have to resort to firing up Windows under VirtualBox every time I add/remove a track from my player.

---

### Post by shakey on 2007-12-11
I have one of these players, and after some tinkering, I found the file database on the player is stored in what looks like a tab-delimited text file. So as far as I can tell, if I/someone has the time, all that needs doing is writing a simple program to parse this file. Adding new songs would then be a simple matter of drag+ drop files, then run a script to update the database.

The file in question is <device>/MYMUSIC/DB/K2.GDD
To add music, the files need to be copied to <device>/MYMUSIC/K2/

Hope this helps.

edit:    progress, I've managed to write code to convert the database file into a normal tab delimited spreadsheet, now to try to go the other way...
edit2:  bah! there's 6 numbers at the start of the database file that need to be correct for it to work, yet I have no idea what they are.

---

### Post by davenims on 2007-12-12
I was messing with this earlier in the year with the intention of writing some software to replace the very poor program that is supplied with the MP3 player.

Rather than being a tab-delimited file, I believe the K2.gdd file is more like an old-style database with a set number of characters for each field - hence the different lengths of space between the columns.

I was tinkering for a while and I believe that each entry is entered into the file like a database with set text field lengths as follows:

[B]Folder Name [28]
DOS File Name [12]
Song Title [64]
Album Title [64]
Band Name [64]
Genre [30]
Date MMYYYY [14][/B]

You need to enter however many spaces after each field to make it up to the length in brackets.

However I tried adding a file into the K2 folder and entering these details, and it just stopped the player from playing any files at all, and I still couldn't see the new track on the player, so something else is missing.

I don't know whether it is something to do with the characters at the start of the file, as someone said above, or if it's something to do with the other files in the DB folder (ALBUMS etc) or both.

If anyone can figure this out I will knock up a small program and share it, as the Vusys/AGCI website seems to have disappeared now and I don't think any updates will be forthcoming.  I guess they must have gone bust or something.

ps. I'd highly recommend backing up all the files from the DB folder before you start doing anything!

---

### Post by shakey on 2007-12-12
As far as I can tell, the issue is the 6 characters at the start of the file. I suspect these are actually numbers, and since they're in groups of 2 they could even actually be 3 2-byte integers. When the number of songs in the database changes so do these values. As to what they actually mean I have no clue.

---

### Post by shakey on 2007-12-12
progress, the first 2 of the 6 numbers is the number of tracks, as a 2-byte integer with the lower byte first.

---

### Post by davenims on 2007-12-13
Ah yes you seem to be right.

There's something going on in the first line of each of those LDD files aswell after each transfer.

I think again the first two digits is a counter... the number of artists/albums/whatever, maybe?

---

### Post by Vyse21 on 2008-01-22
Hi all, i also have an i-dj 670 - mp3 player - and would love an open source music manager for it, since windows XP no longer recognises it in windows media player, and adding new tracks via drag and drop - does not update the database. The bundled audiophile software is quite clumsy to use and has no updates available for the future. I cannot believe the company would not simply make the specs for the database available.

Good luck.

---

### Post by tamias on 2008-02-05
Some useful information so far, thanks everyone who's been looking into it.

Incidentally, does anyone have a successful strategy for getting this player to play tracks at random from its *entire* library of tracks? For me, the randomly-generated playlist only ever contains a subset of the entire library, whether I choose 'All' in artists, genres, year, etc.

---

### Post by alanandhispc on 2008-05-08
Hi All,

I've been doing some research on this, as i'm interested in writing a ubuntu useable script to do this.

from googling the firmware and database names and locations, i came across this link:

[http://syllogism.co.za/2006/03/Logik-HDD33.html](http://syllogism.co.za/2006/03/Logik-HDD33.html)

> I got a Logik HDD33 a while back, and so far I have actually been pretty content with it. It's small and attractive, and if you don't act like a clout and format the drive without keeping a backup of the firmware, everything is good. The only problem I do have with it is its ability to use play lists. It seems to use its on proprietary format, probably to force you to use their crummy software, but I still don't see the point of it.

However I've recently set about reverse engineering its database format so that I can create play lists for it in whatever operating system I happen to be using at the time. This has proved rather challenging though, since there are quite allot of strange things in the database file.

The file resides in DB/K2.GDD. The device uses this to generate the Album/Artist/Genre/Year etc lists for sorting and effectively using the play list functionality.

So far I have managed to come up with the following methods to successfully read and write the database. All I really need to do now is figure out where it stores play lists themselves, and how to encode filenames (seems to be FAT16 standard 8 character limit).

#!/usr/bin/python
import struct

# Reading in a current DB file..
j = "K2.GDD"
f = open(j, 'r')
dta = f.read()
f.close()

def nulls(n):
    return ''.join(['\x00' for i in range(n)])

def pad(s, n):
    """Pads string s (from struct.pack) to length n"""
    return s+nulls(n-len(s))

def decodeDB(data):
    head = dta[:512]
    locs = range(512, len(dta), 276)

    items=[]

    for i in locs:
        item = dta[i:i+276] # Each entry 276 bytes long.

        folder = item[:28].replace('\x00', '')
        filename = item[28:40].replace('\x00', '')
        songTitle = item[40:104].replace('\x00', '')
        songAlbum = item[104:168].replace('\x00', '')
        songArtist = item[168:232].replace('\x00', '')
        songGenre = item[232:262].replace('\x00', '')
        # The elusive "X", which appears on some entries, different on others, seems to depend on path depth.
        ex    = struct.unpack('!H', item[262:264])[0]
        year = item[264:].replace('\x00', '')

        items.append({  'folder':folder, 
                        'filename':filename,
                        'title':songTitle, 
                        'album':songAlbum, 
                        'artist':songArtist,
                        'genre':songGenre, 
                        'ex': ex,
                        'year':year
                    })

    return items

def encodeDB(items):
    start = struct.pack('<B', len(items))
    # I have no idea what these next bits signify 
    thing = struct.pack('<L', (54516L)) 
    otherThing = struct.pack('<L', (616L))
    head = pad(start, 16) + pad(thing, 8) + otherThing

    def encodeItem(item):
        ret =   pad(item['folder'], 28) + pad(item['filename'], 12) + pad(item['title'], 64) + pad(item['album'], 64) + pad(item['artist'], 64) + pad(item['genre'], 30) + struct.pack('!H', item['ex']) + pad(item['year'], 12)
        return ret

    data = [encodeItem(i) for i in items]

    return pad(head, 512) + ''.join(data)

items = decodeDB(dta)

newDB = encodeDB(items)



im going to have a play with this and also see if i can find the application that comes by default with the player this chap talks about. but thought i'd share what i've found.

Thanks,

Alan

---

### Post by alanandhispc on 2008-05-08
i just ran this in python and did a simple "print items" instead of "newDB = encodeDB(items)" after putting a copy of K2.GDD into the same location as the python module.

the array all printed and looked like it had read everything fine. hurrah!.

it turns out he had finalised this and he is still an active blogger, so i have requested if he could send me a copy of the script, as the link on his site is not working.

im so close to not having to use that stupid jukebox tool in windows...i can just feel it.


Thanks,

Alan

---

### Post by tamias on 2008-05-28
Alan,

Just posting to say I'm still very interested in an Ubuntu-friendly tool for my Vusys MP3 player, so please keep us updated -- your work looks promising!

---

