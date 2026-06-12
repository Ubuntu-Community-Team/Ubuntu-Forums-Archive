---
title: "GRAMPS - save problem"
date: 2008-10-01
forum: General Help
---

### Post by CarlWalters on 2008-10-01
I recently installed GRAMPS (2.2.xx) on my Desktop and Laptop both of which are running Ubuntu 8.04. From first look it seems like it's going to be very useful. I downloaded a .ged file from my on-line tree on ancestry.co.uk and was able to import it into GRAMPS fine. I then tried adding some pictures to the family data. This worked well except that GRAMPS doesn't seem to save any of this new information. There doesn't seem to be a File-Save option anywhere in the menus although there is a File-Save-As option) so I assumed that any new data would be saved automatically. Is this correct or am I hopelessly wrong? Perhaps I should be running a later version?

---

### Post by Buster95 on 2008-10-04
Single click the "people" tab;
Double click the name of the person you want to edit and you get a personal file;
Single click the "gallery" tab of the personal file;
Single click the "+" sign on the right hand side and two dialogue boxes will pop up - one to select the media object (photo) from your files and one to add sources, notes and references to the photo;
Select the photo (or whatever other object you want).

Note that the pathway is absolute so if you change the location of the photo later, GRAMPS will lose the link (I think that this is a problem for organising a backup file but I'm still playing with it).

Also note that the object at the extreme left of the gallery is the one that appears on the personal records and pedigree. You can shift them around as you please.

You can also get to the personal file by double clicking from the pedigree tab (and probably a few other ways I haven't yet found).

Don't worry about the "save". It happens automatically each time you select "enter".

Please understand, I'm no expert - I've been evaluating GRAMPS for a month or so, with a view to moving away from FTM. I'm extremely cautious (perhaps anal) about trusting another genealogy program, but this one looks quite good so far. It's at least as good as any other I've looked at so far, but with somewhat less "bling" than the commercial offerings.

Happy to help further if you need it.
Cheers

---

### Post by CarlWalters on 2008-10-06
thanks for the useful info :) I hadn't realised about the absolute paths so I will keep an eye on that!

I have upgraded to version 3.x.x now and am trying that. I think my problem is that I have managed to get two versions of the same tree imported and I am having problems distinguishing between them. So when I've added a photo I have added it to a duplicate person and then can't find it next time I go into GRAMPS. I don't know if there is a way of setting a "Home" person (i.e me) and having GRAMPS start at that point each time? 

I'd also quite like the descendants to be displayed vertically rather than horizontally - but I haven't found a way of doing that yet.

---

### Post by Buster95 on 2008-10-07
Easy question first: Setting "home" person. Look in the "Edit" pulldown. There's a "Set home person" selection for the "people" view. It's worked well for me.

Regarding duplicates, I also got duplicates when I first imported my GEDCOM file. I don't know what caused it. I initially suspected that it was an artifact of the conversion of the file from the FamilyTreeMaker .ftm format to .ged and then to the GRAMPS .xml format.

However, after labouriously repairing the anomalies (there is a facility under "tools" to repair duplicate persons), I have since noticed what I think may be "new" duplications. The first new events are duplications of JPEG photo objects that I have recently loaded (I just deleted the unwanted objects). The second was duplication of some events (for example: a marriage entry) I have also observed two days ago, that the children of a person had doubled up in "Relationships" view only.

The final issue that I'm looking into is that my system has crashed twice in the last two days while using GRAMPS. According to my /var/log/messages and /var/log/syslog, it may be related to an hourly cron event. I'll be seeking some guidance from the GRAMPS gurus on that one.

Perhaps I've given you more grief than help here, but I did mention earlier that I've just started evaluating the GRAMPS system. This may be just part of the learning process.

Cheers

---

