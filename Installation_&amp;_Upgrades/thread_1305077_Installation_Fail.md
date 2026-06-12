---
title: "Installation Fail"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Devon64327 on 2009-10-29
I've been trying to install of Karmic Koala on my PC all day and I've wasted 7 CDs. I'm currently running Jaunty and I know I can just upgrade but I prefer to do a clean install to clear out a lot of crap Ive accumulated. Ive downloaded and burned the ISO 7 times but when ever I choose to install in the CD boot menu it freezes. The same thing happens when I try to Check the disk and choose the Try me option. Im using the default Braseo disc burner and when I finish I always get this error. 
> 
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_1PQG2U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_52UK2U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_RRRK2U.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/devon/Desktop/ubuntu-9.10-desktop-i386.iso (size = 54674072)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 67e063e2377a0f7fbdc9bf907dd63c27 ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr0
    speed=48
    driveropts=burnfree
    -dao
    fs=16m
    -data


And it tells me my file may be corrupt. Im getting really sick of trying this so any help would be appreciated. Thanx

---

### Post by louieb on 2009-10-29
> speed=48

I burn at 2x, 4x tops. All it takes is a few twisted bit to turn a CD into a coaster.

---

### Post by Devon64327 on 2009-10-29
I went into the options menu and it gave me two options... Highest and CD

---

### Post by arpanaut on 2009-10-29
> **Devon64327 said:**
> I went into the options menu and it gave me two options... Highest and CD

I had this speed problem in Jaunty with the default burner (Brassero) when I was trying to burn some iso's recently and had to install GnomeBaker to get the option of different speeds...  

Hope this helps!

---

### Post by Devon64327 on 2009-10-29
can i find this in the repositories?
Edit--- NVM i got it

---

### Post by twright on 2009-10-29
Simple, just use a usb stick instead.

Otherwise every Linux magazine should be giving out Ubuntu CDs at the moment.

---

### Post by Devon64327 on 2009-10-29
> **twright said:**
> Simple, just use a usb stick instead.

Otherwise every Linux magazine should be giving out Ubuntu CDs at the moment.

No offense to everyone who does/is but im not a linux freak and i dont subscribe i just prefer ubuntu over windows and my flash drive is corrupt so its just cds for now

---

### Post by twright on 2009-10-29
> **Devon64327 said:**
> No offense to everyone who does/is but im not a linux freak and i dont subscribe i just prefer ubuntu over windows and my flash drive is corrupt so its just cds for now
Neither am I (OK, maybe) - they are just an easy way to get working disks :-)

If you check the md5sum of the downloaded file, does it match to one on the website? (google it).

---

### Post by Devon64327 on 2009-10-29
:( no...

---

### Post by arpanaut on 2009-10-29
> **Devon64327 said:**
> can i find this in the repositories?

Yes it is, In the terminal just copy&paste, 

```
sudo apt-get gnomebaker
```

hit enter, type in your password,enter again, done

P.S. your password will not appear but it will work.

---

### Post by twright on 2009-10-29
> **Devon64327 said:**
> :( no...
Um, no to what?

If the sums don't match then you need to download again...

---

### Post by arpanaut on 2009-10-29
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

If you don't know how.

---

### Post by Ijtaba on 2009-10-29
There are ways to mount an image off your hard disk with grub.. unless youve got too many useless cd's, in which case keep doing what your doing

---

### Post by intelliboy on 2009-10-29
I am also facing the same problem. I downloaded kubuntu karmic and burned it using k3b. I've gone thru 5 cd's so far including one for ubuntu and one for the alternate cd. Pretty much all of them exihibit the same behavior. The system boots of the cd, i get the main boot screen and then no matter what option i select, it goes to a blank screen with a blinking cursor on the top left and stays there.


> **Devon64327 said:**
> I've been trying to install of Karmic Koala on my PC all day and I've wasted 7 CDs. I'm currently running Jaunty and I know I can just upgrade but I prefer to do a clean install to clear out a lot of crap Ive accumulated. Ive downloaded and burned the ISO 7 times but when ever I choose to install in the CD boot menu it freezes. The same thing happens when I try to Check the disk and choose the Try me option. Im using the default Braseo disc burner and when I finish I always get this error. 


And it tells me my file may be corrupt. Im getting really sick of trying this so any help would be appreciated. Thanx

---

### Post by intelliboy on 2009-10-29
To add more info, i burned the cd's on windows using imgburn and on my existing kubuntu using 9.04. Imgburn verifies the image and reports no errors. In k3b, when i select the "verify data" option, it always complains that the data on track 1 is different than the image file. It gives this error no matter what.



> **intelliboy said:**
> I am also facing the same problem. I downloaded kubuntu karmic and burned it using k3b. I've gone thru 5 cd's so far including one for ubuntu and one for the alternate cd. Pretty much all of them exihibit the same behavior. The system boots of the cd, i get the main boot screen and then no matter what option i select, it goes to a blank screen with a blinking cursor on the top left and stays there.

---

### Post by Devon64327 on 2009-10-29
<<<
<<<
<<<
FIVE!
FIVE CUPS O UBUNTUUUUU


Got it to work! I used gnomebaker and it took a while but I made a succesful live CD!
Thanx for your help!

---

### Post by louieb on 2009-10-29
@[B]Devon64327

Nautilus file browser - Right click on the iso and choose - write to disk.  Should give you more write speed options.

OPPs - to late. :popcorn:

[/B]

---

### Post by Devon64327 on 2009-10-30
Well now when i try to boot it doesnt even bring me to the boot screen. it freezes when i tell it to boot from disc.
I used a bittorent they suggested and i used gnomebaker to mount it but i couldnt check the hash as it was too confusing.

---

