---
title: "Files restored from linux file server unable to be accessed under linux"
date: 2008-09-26
forum: General Help
---

### Post by LittleFoot on 2008-09-26
I took my hard drive and copied all the files that I though I would need from it to the ubuntu server I have set up. Used cp to transfer the files.

Using a live cd I copied all of the files back onto the hard drive.

Now when I go into the disk on the machine with the windows disk I get access denied to all files and folders.

I took the hard drive out and hooked it up to a windows machine and tried to take ownership of all the files with the administrator account.

Back to the windows recovery on the laptop with a new drive and with the file permissions supposedly changed, I still receive access denied to all the files.

Edit->  Oddly enough I have full access when I hook the drive up to a windows computer running in safe mode.

I can't finish repairing the system if I cannot get these files to access.

Any suggestions?

---

### Post by hyper_ch on 2008-09-26
two things:

- when you copied the files did you tell to copy also the file permissions/ownership?

- did you backup the files onto a non-linux filesystem?

---

### Post by LittleFoot on 2008-09-26
When I copied the files originally I used

cp -r -H source dest

source being the original failing drive with ntfs
dest being the shiny new drive formated ntfs

copying them back was pretty much the same but with source and dest switched.

The problem could have been with the way I mounted the drive originally as well from what I've been reading.

sudo mount /dev/sdc1 /media/disk

as it was mounted via sudo I'm guessing it inherited root file permissions.

I finally was able to get into the important folders by taking the drive back out and recopying all of the files I needed via a running windows computer with the drive plugged in locally, from the server via samba to the drive.

when I attempted to copy the files via the ubuntu live disk all files access denied when mounted with windows recovery console post restore.

I know I'm going to have to do this again, and I would much rather be able to restore files from the server through a live cd back to the new drive in a system instead of taking the drive out and restoring things through a working windows computer that isn't always going to be available.

I think I need to figure out how to write files to an ntfs drive with the ability to make them readable by anyone that can access the drive, especially the recovery console.  Not sure how it works though, still not sure what went wrong.

backed up as follows
ntfs -> ext3
ext3 -> ntfs

---

### Post by LittleFoot on 2008-10-01
bump still need an answer
Have to do the same thing more or less again without a windows computer to filter things through to remove permissions.

---

