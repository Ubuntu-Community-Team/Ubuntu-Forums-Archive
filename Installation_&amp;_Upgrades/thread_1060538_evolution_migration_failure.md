---
title: "evolution migration failure"
date: 2009-02-04
forum: Installation &amp; Upgrades
---

### Post by gozzerd on 2009-02-04
I am trying to change machines and move all my old stuff over.
 
My starting point is 8.04 ubuntu, but I added the ubuntustudio stuff to it. I have been using Evolution for a little over a year on this installation and have about 1.3gb in my mail. The machine is dual p3 1ghz with 1gb ram, so 32 bit.

My new machine is an AMD phenom quad 9650, with 4gb ram. The new drive is a 500gb sata drive, with lots of partitions. I did a fresh install of Intrepid amd64 Desktop. The install went wonderfully well for the most part. I popped my two old ide drives in the new box to facilitate transfer. The intrepid installer did great, finding my 8.04's grub install, and setting grub up beautifully. It saw my 8.04 evolution installation and I thought it was going to migrate everything to the new disc. 

But the only thing that made it was the account info. None of the mail or mail folders, or contacts/addressbook info made it. I opened and closed a bunch while it kept downloading mail from the net,and populating a new inbox, but nothing else worked. 

I googled and found several 'how to' pathways for migrating, but they have all failed. Backing up the Hardy/32 bit evolution and restoring to the Intrepid 64 bit install didn't work. That only operated on the .evolution file, not the gconf or gnome db files. 

I did the debian procedure of stopping gconf2 and evolution first, then tarring and untarring a couple of the gnomish files along with .evolution, but that did not work.  I think that was when I got the camel error when trying to restart evolution. I had to use a terminal to see anything and there was a complaint from 'camel-something' about being unable to allocate over 3gb of memory. It referenced bad calls from glibc. There was a bug filed on this already.

I then read another procedure on the bug page, where you removed the .evolution file, restarted evolution, then replaced the newly generated .evolution with the old that has your mail in it. This seemed to work. I spent the morning doing my work in the new installation, but on logging out and back in, or else rebooting, don't remember which, evolution started with the first time page. I tried several things to change the behavior, but to no avail. Then I read the start page carefully. It was suggesting I proceed with a restore. I had the old archive from the first attempt in my home directory, So I did that to see what would happen, and it was back to the camel memory allocation error. 

Isn't there a way to get my new 64 bit Intrepid evolution to use my old 32 bit Hardy mail data?

Thanks

Geoff

---

