---
title: "Take ownership of documents and settings"
date: 2008-07-20
forum: General Help
---

### Post by bobie on 2008-07-20
I installed Ubuntu on my desktop and I want to copy my files from my user folder in XP from a seperate HD. 

I tried the code sudo chown barry /media/sambo/documents and settings/barry
(barry is my ubuntu user. sambo is the hard drive. barry is the user folder)

I enter my sudo password and get "cannot access '/media/sambo/documents': No such file or directory"
"cannot access 'and': No such file or directory"
"cannot access 'settings/barry': No such file or directory"

I tried renaming the documents and settings folder without the spaces and I tried a variation of CAPS and non caps.

---

### Post by CatKiller on 2008-07-20
You can use Tab-completion if you aren't sure how a file or path should be represented. So you could use sudo chown b<TAB> /me<TAB>/s<TAB>/Do<TAB> to fill in the full path. If there's more than one way to complete the file/path/command, the terminal will beep. A double-tap of Tab will show you all the ways that the line could be completed. Spaces are normally 'escaped' with a \, as in Documents\ and\ Settings.

Having said that, you shouldn't need to change the owner of the source on a copy. You might need to change the permissions of the files once you've copied them. Also, given that the files are your Windows ones, and so are on a FAT or NTFS partition, trying to change the owner to some arbitrary user on some other Operating System is probably pretty meaningless as far as those file systems are concerned.

The easiest way to copy files that only root has access to is to open a File Manager window as root with ```
gksudo nautilus
``` Also, if this is a drive that you might want to access regularly, you might consider setting up your /etc/fstab so that it can be used by normal users.

---

### Post by silkstone on 2008-07-20
This may not be the main problem, but...

Spaces in folder/directory/file names are not recognised as part of the name in Linux. Ideally you should use a hyphen or underscore instead of a space, but otherwise you have to put quotes around everything...

sudo chown -r barry:barry "/media/sambo/documents and settings/barry"

---

### Post by bobie on 2008-07-20
Thanks for the reply.

When I would try to copy them I got an error. "error copying the file into /home/barry/desktop" more details gives me "Permission denied" Which is why I thought I needed to take ownership. I tried gksudo nautilus and it brought up a file browser window with root as the home directory, but when i tried copying and pasting i get the same error. And it's not that I don't have access completely to my drive, it's just certain files that I can't get to.

---

### Post by CatKiller on 2008-07-20
Well, I can't help you directly. I know (from experience :rolleyes:) that that particular dialogue box is not expecially informative. For example, I subsequently discovered that the reason I couldn't copy some files to a FAT partition was because FAT can't handle links. But all the information that dialogue box gave me was that same Permission Denied message.

The root user has full access to all files (with one or two deliberate exclusions) so I don't think it's necessarily a permissions problem as such. Root should definitely be able to write to your Desktop unless you've specifically set the Desktop folder to be read-only. And root can certainly write to their Home folder (/root) so you should be able to paste there.

If you can identify which particular files are causing problems - assuming it's just a few - perhaps someone with more specialised knowledge would be able to help you identify why those are different, and whether there's anything that can be done about them.

---

### Post by bobie on 2008-07-20
Still no luck. quotes don't do it for me. tab-completion doesn't work and gksudo didn't work.

---

### Post by CatKiller on 2008-07-20
> **bobie said:**
> Still no luck. quotes don't do it for me. tab-completion doesn't work and gksudo didn't work.

In general, case is important, so "Desktop" is a different directory than "desktop". That might be why you aren't having any luck with the quotes.

In what way did tab-completion not work?

I think we've exhausted all the general information now, without specifics of exactly which files are being copied, from what type of filesytem, how that filesystem is mounted, where the files are being copied to, which filesystem the target is on, how that filesystem is mounted, which commands you're using, and so on.

Hopefully someone else can give you more insight than I can.

---

### Post by mc4man on 2008-07-20
Are you not able to browse to your xp partition and do a copy and paste of what you want onto your desktop?
If i wanted to cli something specific  from my xp partition I'd do as such (copy a file vlcrc)
 > cp /media/WINDOWS/'Documents and Settings/doug/Application Data/vlc/vlcrc' /home/doug/Desktop
or for a folder (My Documents)
> cp -R /media/WINDOWS/'Documents and Settings/doug/My Documents' /home/doug/Desktop


---

### Post by Tim Sharitt on 2008-07-20
The spaces in filenames must be escaped in the terminal using '\'.
```
sudo chown barry /media/sambo/documents\ and\ settings/barry
```

---

### Post by bobie on 2008-07-20
Thanks for all the suggestions, but I'm still not having any luck. Here's the latest.

I tried first made sure I have caps where they should be and spaces escaped with \. Then I tried the cp command. It put a folder on my desktop and started filling it with things, but then did the same thing that a copy and paste in the GUI was doing. I get a bunch of "permission denied" errors. It seems like I need to be SOMEHOW changing permissions on the folder, but I'm unable. chown hasn't worked. Is chmod something I should be trying? If so, what is the syntax?

---

### Post by bobie on 2008-07-20
By the way--  I don't know if this is normal, but when Terminal asks me to put in my sudo password, I do, but the cursor doesn't act like I'm inputing anything. It stays and flashes.

---

### Post by Tim Sharitt on 2008-07-20
One more thing to check, is it "documents an settings" or "Documents and Settings". Filenames are case sensitive.

---

### Post by Tim Sharitt on 2008-07-20
> **bobie said:**
> By the way--  I don't know if this is normal, but when Terminal asks me to put in my sudo password, I do, but the cursor doesn't act like I'm inputing anything. It stays and flashes.

Yes, that is normal.

---

### Post by bobie on 2008-07-20
Yeah. All of caps are in the right places. Any other ideas why this won't work?

---

### Post by Tim Sharitt on 2008-07-20
I probably should have asked earlier, but is the drive mounted read-only?

---

### Post by bobie on 2008-07-20
Ok. So I typed *exactly* sudo chown barry /media/Sambo/Documents\ and\ Settings/Barry   Terminal went down one line like it worked, but when I again tried to copy and paste I get a bunch of files that say permission denied and the owner of said files is set to root.

---

### Post by bobie on 2008-07-20
hmmm....how would I check that?

---

### Post by Tim Sharitt on 2008-07-20
run the chowm command with the -R option to change the ownership of the files inside.
```
sudo chown -R barry /media/sambo/documents\ and\ settings/barry
```

---

### Post by bobie on 2008-07-20
Right. Left out the -R. But it errors out and says permission denied. On the permissions tab for the drive (or any of the files inside) it of course shows root as the owner and group. But for others it says Read and Write, but it's grayed out.

---

### Post by bobie on 2008-07-20
Thanks for putting up with me. this is frustrating. I'm normally especially savvy with computer's/code, but I'm new to Ubuntu and so far it's getting the better of me.

---

### Post by Tim Sharitt on 2008-07-20
type in
```
sudo mount | grep -i sambo
```
and post the results

---

### Post by bobie on 2008-07-20
/dev/sda1 on /media/Sambo type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by Tim Sharitt on 2008-07-20
I suppose you could just change the permissions
```
sudo chmod g+rwx /media/sambo/documents\ and\ settings/barry
```
to give read-write-execute privileges to the root group, which you should be a member of. If you're not, add an o to the options to make it go+rwx.

---

### Post by bobie on 2008-07-20
Sorry. Nope. Still says I don't have permission. I tried both with and without the o. 

I tried gksudo nautilus and when I try changing permissions on the permissions tab in properties it acts like it doesn't want to change. It also won't let me change the owner to barry. When I try it immediately changes it back to root.

---

### Post by Tim Sharitt on 2008-07-21
Well, I'm afraid I'm out of ideas for now, sorry. I'll get back to you if I can think of any thing else. I just don't have much experience with ntfs partitions.

---

### Post by mc4man on 2008-07-21
> /dev/sda1 on /media/Sambo type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)  That seems to indicate you have full permissions (read, write, access, delete)
In any event you'd only need read/access to copy _from_, maybe you should look at where you're copying to.
 Why don't you try copying something to your xp partition to see about read,write there.

---

### Post by bobie on 2008-07-21
I'm able to copy to the partition just fine.

---

### Post by mc4man on 2008-07-21
Try something really simple, browse to anywhere on your xp partition, grab a file with your mouse and try to drop it onto your desktop

---

### Post by bobie on 2008-07-21
That works for some files, but not others. Specifically ones in the Documents and Settings folder. But it's still just some. THere are files/folders from my docs and settings folder that I can copy/paste, but others give me the permission denied error. But I haven't found any outside of that folder that are a problem. Although, I haven't tried copying and pasting much outside of there.

---

### Post by mc4man on 2008-07-21
can you give an example of a file or folder you can't copy ?
I just copied the whole documents and settings directory no problem

edit: or you could boot to windows, copy to removable media or try copying directly to your ubuntu install from there. There are several progs for win that will give that ability (assign a drive letter, ect.)

---

### Post by bobie on 2008-07-21
An example of a file that I've been using as a general test to see if something worked is in my (xp) desktop folder. "seatoolsforwindowssetup.exe" 

I wouldn't mind copying from xp into ubuntu, but I tried that and XP didn't assign a drive letter to the Ubuntu drive/partition. If there is a program that will do that for me and allow me to boot to XP and copy over my files I would be interested in that.

Thanks

---

### Post by mc4man on 2008-07-21
[http://www.fs-driver.org/](http://www.fs-driver.org/)
works with Ext3 also
I haven't found any problem transferring files back and forth (usually just AV stuff. I would refrain from deleting files,ect from one OS to an other. If absolutely necessary use shift-delete
> 
 seatoolsforwindowssetup.exe who knows, exe's aren't an issue per se

edit: for the hell of it just transferred seatoolsforwindowssetup.exe from xp to ubuntu from ubuntu side, no issues there, though it's nothing you could use anyway.

---

### Post by silkstone on 2008-07-21
You need to use **chown -r** to change the ownership of everything within the folder. the -r means 'recursive'.

---

### Post by bobie on 2008-07-22
I was using the seatools file to just test. I wasn't hoping to use it in Linux. But, I'v downloaded Ext3 and it seems to be working for me. I'm copying the files over that I wanted to get at without any problems. I still don't understand why I could copy them from Linux, but it all worked out. THanks for all your help.

---

### Post by mc4man on 2008-07-22
> I still don't understand why I could copy them from Linux Definitely something with the files themselves not your install.

---

### Post by bobie on 2008-07-22
Ok. Thanks. I probably changed some security setting in XP along thhe way and now don't remember. Whatever though, I got the files I needed. 
Thanks again.

---

