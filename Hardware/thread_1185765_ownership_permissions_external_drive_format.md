---
title: "ownership permissions: external drive format"
date: 2009-06-12
forum: Hardware
---

### Post by knomaly on 2009-06-12
Computer: Lenovo T500
 Operating System: Ubuntu 9.04
 External Hard Drive: 250GB Maxtor OneTouch 4 Mini
 

 I recently purchased the external Maxtor hard drive cited above that I would like to backup data to from my notebook computer. But before using the drive for this purpose, it is necessary to reformat the drive to something other than the manufacturer's preformatted file system type: NTFS.  For this purpose, I chose to reformat the drive to ext3 using GParted, to match the default Ubuntu 9.04 file system type selected during OS installation.  
 

 The drive reformat process I used is as follows: I plugged the drive in, unmounted it, and then ran GParted via its GUI. From GParted, I created a new partition table (Device > Create Partition Table), and then formated the "unallocated" drive to ext3, leaving all other settings in their default mode. Upon completion of the format operation, I then closed GParted, unplugged the drive, waited a few seconds, and plugged the drive back in. Ubuntu properly detects the device, and invokes the Nautilus file manager with the drive selected and the right pane displaying a "[FONT=DejaVu Sans, sans-serif]>[/FONT][FONT=Times New Roman, serif]lost+found" file.[/FONT]
 

 The problem I have encountered, is that the drive's Owner and Group permissions are set to root. This is made evident by the fact that a new folder within the file system cannot be created, and by what is displayed in the Permissions tab of the file system's disk Properties: Owner: root. Group: root.
 

 Please note that I used the same drive format procedure to format the drive to fat32, and the following permissions were granted by default: Owner: "home folder". Group: root.
 

 What I would like to know is as follows:  
 

 I. Is the external drive format procedure I am using valid?  
 

 A. If valid, then why are both the Owner and Group Permissions set to "root" by default?  
 

 1. What is the recommended procedure for changing the ownership permissions from "root" to that which corresponds to the name of my home folder?
 

 2. Can this be done through Gnome's file manager GUI rather than the command line?  
 

 a. If "yes", then how?  
 

 b. If "no", then why not?
 

 B) If invalid, then what is the recommended procedure? Please explain in detail.
 

 Thanks for your kind attention!

---

### Post by labinnsw on 2009-06-12
> I. Is the external drive format procedure I am using valid?  
Yes
 

>  A. If valid, then why are both the Owner and Group Permissions set to "root" by default?  
Becuase you had to be root to perform the operation.
 

>  1. What is the recommended procedure for changing the ownership permissions from "root" to that which corresponds to the name of my home folder?

Open a terminal and type:

```
sudo nautilus
```

Supply your administrative password
Navigate to the drive
Right click and select properties
Under the permissions tab, change the owner.
 
> 
 2. Can this be done through Gnome's file manager GUI rather than the command line? 

Yes
 

>  a. If "yes", then how? 

See instructions above
 

>  b. If "no", then why not?

Not Applicable
 

>  B) If invalid, then what is the recommended procedure? Please explain in detail.

Not Applicable

 Thanks for your kind attention![/QUOTE]

---

### Post by knomaly on 2009-06-13
Thanks labinnsw! That worked perfectly. 

A couple of things. . .I'll describe them in reverse order:

1) The need to authenticate the drive. Very interesting. I selected the always authenticate when connected option. (Honestly, I should have taken a digital photo of this dialog box to use as a reference for the exact language used, but I believe that approximates what is written for one of the drive authentication options.)

2) Could you kindly define the permission settings. I just changed the Owner and Group permissions from root to the home folder. But what about the Folder Access settings for the Owner and Group, and the File Access settings for all three: Owner, Group, and Others? I see the following options: None, List files only, Access files, Create and delete files, and -----.

Also, could you kindly address the meaning of the Execute and SELinux context settings, as well as the function of the "Apply Permissions to Enclosed Files" button, in reference to the proper setup of an external HD for local users.

3) Navigating to the drive. The drive identification was different, if I recall correctly. (Another thing I should have made note of.)

Thanks for your kind attention.

---

### Post by labinnsw on 2009-06-14
I am in a hurry at the moment but, if you keep an eye on the space, I will respond in the next 24 hours if no one else responds in that time.

---

### Post by labinnsw on 2009-06-15
> 1) The need to authenticate the drive. Very interesting. I selected the always authenticate when connected option. (Honestly, I should have taken a digital photo of this dialog box to use as a reference for the exact language used, but I believe that approximates what is written for one of the drive authentication options.)

Not sure if you are asking a question here but this is a level of security.

> 2) Could you kindly define the permission settings. I just changed the Owner and Group permissions from root to the home folder. But what about the Folder Access settings for the Owner and Group, and the File Access settings for all three: Owner, Group, and Others? I see the following options: None, List files only, Access files, Create and delete files, and -----.

I usually give myself ownership of those places allocated for storage. I do not feel competent to explain this satisfactorily, so I would recommend that you refer to [The Official Ubuntu Documentation]("https://help.ubuntu.com/")

> 
Also, could you kindly address the meaning of the Execute and SELinux context settings,

Sorry, I don't have a clue.

> as well as the function of the "Apply Permissions to Enclosed Files" button, in reference to the proper setup of an external HD for local users.

Will apply the permission settings of a folder/directory to whatever is contained in that folder/directory.

> 3) Navigating to the drive. The drive identification was different, if I recall correctly. (Another thing I should have made note of.)

I am not sure what the question is here.

---

### Post by knomaly on 2009-06-15
The problem with file permissions explanations like that offered by the Gnome foundation ( [http://library.gnome.org/users/user-guide/stable/nautilus-permissions-overview.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-permissions-overview.html.en) ), Keir Thomas and others, is that default file settings for the standard working files and folders* created on machines for home use are rarely, if ever defined in detail. Considering the potential for default settings to change, it would be nice if some visual or other references could be offered that users like myself could examine to quickly verify that their file and folder properties, including permissions settings, are correct, for both security and usability purpose. 

*standard working files and folders: default home folders, example files (plain text, email, open office), external drives, etc.

---

### Post by labinnsw on 2009-06-16
I am sorry, I am unable to help in that regard. I don't even know enough to make a decision to agree or disagree with you. I am a user only. I have no technical training. Everything I know was learned from experience and a little bit of reading.

I subscribe to Linux magazine which is too technical for me most of the time, (planning to cancel my subscription) and Linux format, which is more suitable for my level. The good thing about both magazines is that they both do monthly book reviews. I would recommend you either subscribe or pick them up if and when you can. 

Amazon is a good place to look for any book they review that you might be interested in.

If you feel sufficiently committed, you could even consider pursuing an Ubuntu or Linux course. I wanted to do that but I did not have the necessary programming prerequisite.

Hope you find an explanation that works for you soon.

---

### Post by knomaly on 2009-06-16
Thanks again, labinnsw, for your past support and in providing a better understanding of your linux knowledge. Honestly, I was hoping to elicit a response from an ubuntu forum member knowledgeable about file and folder properties. Run an online search and examine contemporary books dedicated to learning linux. I doubt you will find a detailed explanation or pictorial of the default file and folder properties set for major linux distros. This strikes me as a peculiar black hole in the "accessible" linux knowledge base, as most of the explanations that approach what I am seeking are copyrighted. Preferably, I would llke to see some visual references, in the form of screen shots displaying the default folder properties. Think of it as a component of an exploded diagram of how linux, and particularly ubuntu linux, works.

---

