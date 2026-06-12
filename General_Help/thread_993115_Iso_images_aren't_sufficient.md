---
title: "Iso images aren't sufficient"
date: 2008-11-25
forum: General Help
---

### Post by M4rotku on 2008-11-25
Hello all,

I seem to keep running into problems with ISO images.  The first problem will be the easiest to solve as far as I know.  I have several games that I would like to be able to play without inserting the disks.  This would allow me to play during a bumpy car ride.  I fully own these games.  Thus, I think it would be reasonable for me to be able to make an .iso image of the disk and then mount it using the standard "mount -o loop" command.  However, somehow the games know that this is not the real disk.  When I mount the Warcraft III image and click on the windows executable via wine, I am informed that "Warcraft III was unable to detect a disk in your disk drive."  I checked my wine settings and the .iso is mounted in the right place to correspond with the cd-rom drive.  This has also happened with other games.

The second problem that I am having is that I am not able to create an ISO image of the disk of my favorite game.  The disk is rather scratched and Brasero and all of the other applications I have tried have reported errors and failed to create the .iso.  Is there any way to create the .iso in a manner that the errors are ignored?  The disk works fine regardless of the scratches.

Much thanks,
M4rotku

---

### Post by oldos2er on 2008-11-25
You could try running the program dvdisaster against your scratched disk, to create an error-free ISO.

---

### Post by mkvnmtr on 2008-11-25
DVDiaster is you best bet to get a ISO from your disk. If I owned a game I would not have any problem getting a back up from another source. If the game was mine I also would not have a problem looking on a forum where I found my back up for help mounting the ISO. I hope I have stayed within the guide lines .

---

### Post by M4rotku on 2008-11-25
mkvnmtr, the game with the scratched disk is old.  I don't think they make disks of them anymore.  I know that the company 3DO is still around, but I haven't tried to contact them.  I know it is possible to buy a used copy online, but I am not interested in spending $20.

---

### Post by M4rotku on 2008-11-25
Dvdisaster didn't have the capability to do what I am looking for.  I have the disc, I need to make the iso.  Dvdisaster seemed as though it was intended to fix iso images after they are already created.  I haven't been able to create the iso yet.  The problem is not that Brasero is making the iso and then the iso has errors, it is that because of the scratches on the disc, Brasero is not even able to make the iso.

Are there any other solutions out there that could work?

I just need an iso-making program that is willing to ignore the scratches on the disc.

---

### Post by SPr on 2008-11-25
Have you tried mounting the iso on /media/cdrom? I have no idea whether that is an advisable thing to do. (Sorry, I've re-read your post and it sounds as if you are already doing that.)

---

### Post by prshah on 2008-11-25
> **M4rotku said:**
> 
I seem to keep running into problems with ISO images. 

mount it using the standard "mount -o loop" command.

I think that you need to add the "-t iso9660" option to have the mount treated as a CD device.

I'd suggest you use the program "gmount-iso" from the repos (it's just a python frontend to loopmounting ISOs, and see if the images are then recognised. Remember to enable the "drive" in Wine's config program.

---

### Post by kanikilu on 2008-11-25
I don't know if you are going to find a program that can "ignore" physical damage to a disc...

I haven't used either the toothpaste or Pledge methods, but people say they might work:

[http://lifehacker.com/software/macgyver/macgyver-tip--smooth-a-scratched-dvd-with-pledge-190634.php](http://lifehacker.com/software/macgyver/macgyver-tip--smooth-a-scratched-dvd-with-pledge-190634.php)

---

### Post by CatKiller on 2008-11-25
> **kanikilu said:**
> I haven't used either the toothpaste or Pledge methods, but people say they might work

I once used metal polish on a really tangentially scratched cd, and it seemed to be working rather well until I snapped the disc. If you use this method, put the disc on a flat surface. Don't have it balanced on the fingers of one hand while you're polishing the middle with the other hand.

Always use radial strokes (from the centre out) rather than tangential strokes (round and round) since the disc is read in a spiral, and short gaps caused by radial scratches can be corrected for with the built-in error-correction, but tangential scratches will take out a whole chunk of data.

Polish gently. You want to gradually take away the layer of plastic until the scratches aren't very deep, not remove it one go.

---

### Post by CatKiller on 2008-11-25
> **M4rotku said:**
> When I mount the Warcraft III image and click on the windows executable via wine, I am informed that "Warcraft III was unable to detect a disk in your disk drive."  I checked my wine settings and the .iso is mounted in the right place to correspond with the cd-rom drive.  This has also happened with other games.

It's perfectly fine to use a modified version of the executable to remove the cd checks. In some cases, it's a pre-requisite, since the copy protection only serves to stop the games working in Wine. Megagames.com has a lot, but there are plenty of other sites that have no-cd files.

Heck, even games publishers have been known to use community-produced hacks to remove the copy protection from their own games.

---

### Post by cariboo on 2008-11-25
Check around at the various video outlets in your area. In the small town (pop. 11,000) where I live there are 3 outlets that have the equipment to resurface a disk they usually charge between $5-$10 for this service. I have used them a couple of time when my [Skip Doctor]("http://www.amazon.com/Digital-Innovations-Skipdoctor-Repair-Kit/dp/B00005B9W6") was not enough to repair a disk.

Jim

---

