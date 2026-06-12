---
title: "https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/200462/comments/18"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by SlackBrane on 2009-04-02
Permissions as set up during install.

keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-03-05 12:10 cdrom0
drwxr-xr-x 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

Change the permissions

keith@keith-desktop:/media$ sudo chmod 777 cdrom0
keith@keith-desktop:/media$ sudo chmod 777 cdrom1
keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

Looks 'good'. However having written to a rewritable disk using the unmodified permissions inserting that disk into, in this case cdrom1, causes this to happen....

keith@keith-desktop:/media$ ls -al
total 34
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
dr-xr-xr-x 4 root root 2048 2009-04-02 20:21 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

The previously changed permission for cdrom1 have picked up on the permissions used during creation of the volume and reverted to their original settings. I apologise. Before investigating this further I had had a play trying to 'fix' it so the 'original' install settings as presented here might not be the actual ones. I'm slightly confused that Brasero and other GUI tools were able to write to a blank disk in the first place on a non-root account. Obviously they can but then fall over later. As I say, sorry, I haven't been very stringent about the way I've investigated this. I've been typical me and just started mashing about with things.

If I remove the disk then....

keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

The permissions revert to the ones that I changed them to. This looks good....

In the mean time if you look at the mounted volume properties under Gnome...

[http://www.overkill.talktalk.net/ubuntu/020409/](http://www.overkill.talktalk.net/ubuntu/020409/)
[http://www.overkill.talktalk.net/ubuntu/020409/](http://www.overkill.talktalk.net/ubuntu/020409/)

You can see that I've thrashed about trying to change the permissions that way. Of course it does not work because the system just picks up on the permissions used to create the volume in the first place.

The second picture, of the volume settings, is of interest because the mount options are displayed as ro nosuid nodev noexec and, although I can't fully decipher the meanings is looks like those values relate to the permissions in place when the volume was created and written to, the default install values.

Oh, yes I did try playing about with /etc/fstab like this...

/dev/scd0 /media/cdrom0 auto rw,user,noauto,noexec,utf8 0 0
/dev/scd1 /media/cdrom1 auto rw,user,noauto,noexec,utf8 0 0

I'm not proud so I am happy to admit that I'm no expert and might not know exactly what all that stuff means. However it does not work. In both cases, via fstab or via Gnome, whatever you try to do gets overruled by what was used to create/write to the volume in the first place.

I'll be bold, before I try something, and say it is not really a bug as such, unless, possibly, the ability to write to the disk when the permissions did not allow it is really there. It might be an oversight in setting those default permissions during the install in the first place but they may well be valid choices. Otherwise it might just be irritating. Babble babble.

OK, now I will try something. At the moment, nothing in the drive I have...

keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

With my modified permissions in place and, hopefully operational. I'll use the disk which has already been written to and try to erase it in Brasero. Here we go 3, 4, 6..... There, it is now blank and Ubuntu pops up a dialog saying I have just inserted a blank disk. I don't know how that stands in terms of 'doing the right thing'. If I were to be a security pedant then I would have liked it to come back and tell me I didn't have permission to scrub the disk. It wasn't 'really' mine so I should have been told to get lost..... or maybe not.

Now, moment of truth. If I put the blank disk back into the drive then I get....

keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

So the permissions have not been over ridden, there is nothing on the disk with any permissions, which looks good. Looking at the properties for the blank disk in Gnome gives me...

[http://www.overkill.talktalk.net/ubuntu/020409/](http://www.overkill.talktalk.net/ubuntu/020409/)
[http://www.overkill.talktalk.net/ubuntu/020409/](http://www.overkill.talktalk.net/ubuntu/020409/)

Now I'll use Brasero to put some data on the disk. Here we go 3, 4, 6..... Screeeeeeech :-( Brasero Falls over with an unhandled error!!!!*@%! Very frustrating. Perhaps Braseros' concept of 'erase' does not inflict the right level of armaggedon. I might imagine that at various levels Brasero, and Gnome, think it is a 'blank' disk but when they try and fiddle with it the underlying OS shouts at them.... Then again, from the last ls -al, the underlying OS seem to think... Err, hang on that might be because the disk was not mounted but when it was in order for Brasero to do things to it the OS saw something..... Oooooo whatever.

I can appreciate that there is more to this, beyond what I might know about, than might meet a casual eye.

Right.... I'm not having that. Ubuntu still thinks the disk is blank but I'll get the heavy hammers out and use K3B to force format it. I know I'm just demonstrating my lack of knowledge here but, once again, I am not proud. It's also a good excuse to go twiddle my thumbs for thirty minutes. It still seems strange that, in the same way that Brasero was allowed to 'erase' the disk, K3B is being allowed to totally scrub it.

What if the data was really really important. Then again perhaps my paranoia setting is overly high.

Again, being useless, I've not properly investigated this but Brasero and K3B were throwing up the same sort of 'Unhandled Error' messages. Both could take a 'clean' unused disk and write data to it but efforts to add data to the image broke them. Like I say, if I haven't said it yet I'm guessing that the initial write forced the 'default' permissions. Root owns it and stuff. Then, coming back as someone who is not root and trying to do something with it causes slapped wristies.

70%
75%
80%

I suppose I could just write 85%, 90%, 95%, 100% but I'm doing this in 'real' time...

85%
90%
95%
100%

Yayyyy!!!!

Hmmm, if memory serves, then when I used K3B on a virgin disk and asked it to write data to it on one occassion it managed to write the data and then complained about not being able to eject the disk and there was another one where I asked it to verify the data afterwards and it failed to eject the disk so I pushed the button and it did not try to verify the data. Again, if it is part of the picture, it's like they start out with permission to do what they want but, having done it using the default settings when they come back to do something else they find they no longer own it.

Still hopefully I now have my really really blank disk... Quick, could be fooling myself, check...

keith@keith-desktop:/media$ ls -al
total 36
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

and.... it is not mounted. So, this time I will try Brasero and write some data to it... Drumroll, could be premature but fingers crossed... looking good.... looking good.... fixating.... still fixating........... success!!!!!!!! drive ejects. Phew. Now I'll shunt the disk back in... in the expectation that having written to it with the above permissions it will have those permissions.

And.....

keith@keith-desktop:/media$ ls -al
total 34
drwxr-xr-x 5 root root 4096 2009-04-02 21:44 .
drwxr-xr-x 20 root root 4096 2009-03-05 13:55 ..
lrwxrwxrwx 1 root root 6 2009-03-05 12:10 cdrom -> cdrom0
drwxrwxrwx 2 root root 4096 2009-03-05 12:10 cdrom0
dr-xr-xr-x 3 root root 2048 2009-04-02 23:30 cdrom1
drwx------ 3 keith root 8192 1970-01-01 01:00 disk
-rw-r--r-- 1 root root 110 2009-04-02 21:44 .hal-mtab
-rw------- 1 root root 0 2009-04-02 21:44 .hal-mtab-lock

Right..... I am now extremely bored!!!!!!!!!!! Blimey..... that's frustrating. Then again it probably serves me right for trying to think I might be clever in the first place.

It would seem that, Like what Sebastian says the 'problem' is not trivial in the sense that I'd have a chance. It looks like there is some other 'in between thing' that says NO! and might muck about with other more important things. This is OK though in as much as, as demonstrated, I would not know how to fix it but, now I sort of know it is there, I have the opportunity for a bit of extra 'focussed' thinking in order to work my way around it.

Sorry for being wordy. At the risk of upsetting people I have to say that I look at this and can't help getting the feeling that someone has 'hardwired' something somewhere to sort out a problem elsewhere and ended up breaking this bit. I'm not worthy since I really know nothing but it is really annoying. OK so I am a novice type but if...

Hang on.... Just trying Brasero again on the newly created data disk... This time it lets me add data to it whereas previously it has just fallen over.... and rendered the disk blank. I was about to say that if I was a proper user and was using this to back up stuff then that sort of behaviour would be really dull. This time it has let me do it without moaning. Ooops spoke to early. It's just killed itself again.

With all due respect and appreciation for those who have to deal with this, and the opportunity to admit I am just a basic sort of thicko, I'd like to recommend that..... If the folks at Ubuntu want to make this thing desktop usable for the unwashed majority, and proper people, then this sort of rubbish should not have got in in the first place and it is a priority to get it sorted, patched, delivered and done properly.

I, think, I can almost feel Sebastians' pain for being a frontline bloke with what looks like zero support for something that someone else has decided is 'not important' in their concept of the 'big picture'.

I'll draw a parallel.....

Nero is dirt but the version I got with my new purchase seems to work. This problem, as far as I can see, has crippled any sort of CD/DVD writing software running under Ubuntu in much the same way that my old version of Nero was upsettingly broken. I am therefore forced to assume that someone else is on a different agenda with other 'priorities' whilst being happy to leave 'others' out to hang and dry..... whilst ignoring the possibility, in this case, that Ubuntu has turned into Windows.

ARGHHHHHHHH!!!!

I'd rant some more but I'm drunk again so what's the point?

I've left out the pictures... Could not be bothered.

Keith

---

