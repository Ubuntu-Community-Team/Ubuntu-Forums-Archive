---
title: "Is EASY reinstall-ation an oxymoron?"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by anyboy on 2009-08-03
Short version:
  Where is the HOWTO for EASY RE-installation?  You can save reading the rest of this garbage if you have a good answer to that one!  Yes, I have looked.

Detailed version:
When installing Ubuntu 8.4 (Hardy?) I shrank the XP partition, made root, home, and swap partitions.  I did the separate root and home partitions on the advice that it would be easier to reinstall without losing my "stuff".  What a joke!  

At this point I need to reinstall up-to-date "plain vanilla" Ubunto over UbuntuStudio 8.4 (seems to be difficult to simply upgrade the latter.)

When I tried it I found the **partitioning** stage quite scary and unhelpful.
   a.) It didn't show any old LABELS for my existing ext3 partions.  
         i.) How do I get it to install into my existing root partition?
        ii.) Must I identify/discriminate between these partitions?
   b.) Assuming I have to tell it which partition is which (and I am somehow able to find out myself), is it enough just to use Manual partitioning and to attach the '/' and /Home labels to the correct partitions?  Or what?

Is my current **application software** located in the root partition, and will those programs be destroyed in the reinstall?  I suppose they will be out-of-date anyway...

Assuming I have to replace all of the applications along with the system, 
      i.) Is there some way to automate replacing them?
     ii.) Failing that, is there some way to get a list of everything 
            that is currently installed, so I have something to work 
            from while I manually select them in Synaptic?  
    iii.) What about replacing all the fonts and other related packages 
            and options?

In short, where is the HOWTO for EASY reinstallation?  Surely I'm not the only non-expert who just wants to slip a fresh system into an existing root partition without risking going back to the stone age.  

Or should I just forget about trying to save anything and instead let the installer do what it wants (which is apparently to wipe out EVERYTHING,) plan on replacing my data from the backups, and replace the applications piecemeal (1 hour round-trip journey each time to reach a broadband outlet) as and when I miss them?

---

### Post by pastalavista on 2009-08-03
When you do an installation, always used the 'manual' option and you can create the partitions exactly how you want them. When you first install, create 3 separate partitions (only up to 4 primary partitions or unlimited logical partitions in an extended primary partition). Your main system partition would be labeled '/' at least 10 gigs and no more than 50. The second labeled '/home' should be as large as you need for all the data you want to keep permanently (media, documents & configuration settings) and a swap partition as large as your RAM if you want to use suspend and hibernate effectively.

Now when you need to reinstall, or just want to try a different distro, all you need to reformat is the '/' partition. Don't reformat the /home partition. Uncheck the 'format' box in the _manual_ installation procedure. If you do an automatic installation, the whole disk could be reformatted and you'd lose everything in the '/home' partition. But the manual installation allows you to upgrade much quicker and easier.

To make re-installation of your programs easier, open Synaptic Package manager, click 'status' in the side-pane, select 'installed' find the
non-included programs you want to keep (reinstall first thing) and mark them for re-installation. Then go to the file menu and select 'Save Markings as" and save the file to the desktop to go to a removable media and use it after the re-installation to download every app you want in one swoop. That's about the easiest way I know so far, short of cloning the disk.

---

### Post by mikewhatever on 2009-08-04
> **anyboy said:**
> .........
   a.) It didn't show any old LABELS for my existing ext3 partions. 

/, home and swap are not labels, they are mount points.
 
>          i.) How do I get it to install into my existing root partition?

You need to explicitly point the installer to the root partition.


>         ii.) Must I identify/discriminate between these partitions?

Yes.

>    b.) Assuming I have to tell it which partition is which (and I am somehow able to find out myself), is it enough just to use Manual partitioning and to attach the '/' and /Home labels to the correct partitions?  Or what?

You have to select the appropriate mount point for each partition.

> Is my current **application software** located in the root partition, and will those programs be destroyed in the reinstall?  I suppose they will be out-of-date anyway...

Assuming I have to replace all of the applications along with the system, 
      i.) Is there some way to automate replacing them?
     ii.) Failing that, is there some way to get a list of everything 
            that is currently installed, so I have something to work 
            from while I manually select them in Synaptic?  
    iii.) What about replacing all the fonts and other related packages 
            and options?


Well, destruction is not the term here. The root partition is formatted during the instalation, so that all data on / is lost. You can easily reinstall all packages installed from the repositories using this guide:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

May I also point out that your demanding manner of posting does not inspire much desire to help.
Best of luck.

---

### Post by anyboy on 2009-08-04
Very informative.  Thank you.

According to your description my current partition setup seems adequate.  My remaining problem is that the partition editor in the installer shows two similar ext3 partitions, one of which must be my current root, the other, home.  What I need is some way to i_dentify which partition is which_.

Is there some utility which allows one to explore the **contents** of individual **partitions**?  Presumably the installer only recognizes (or disclose to the user) three things about a partition, 1.) relative position/sequence, 2.) size, and 3.) formatting style/filesystem, which is not much to go on.  

So I would imagine that to be useful for my purpose if someone came up with a "partition browser", it would have to  show the choices in the same order as the partition editor (is it gparted in the installer?) so I can identify them by position in the sequence.

---

### Post by pastalavista on 2009-08-04
You should be able to browse the filesysyem with Nautilus from the live CD. Just open 'Computer' and click on the HDD to mount it.
[I]
Just to prevent confusing yourself in the future, upgrade to Jaunty 9.04 and format the / partition as ext4... it's faster and the /home partition will still be ext3. That's how I did it.[/I]

---

