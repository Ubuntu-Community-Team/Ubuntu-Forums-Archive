---
title: "Memory stick for files between OSs"
date: 2011-02-17
forum: Hardware
---

### Post by PeopleUnite on 2011-02-17
Hey everyone,

I just recently got a Systems76 laptop with Ubuntu  10.10, my first Linux based machine!  My old computer is a Power PC  Mac.  I have a SanDisk Cruzer memory stick which I have been using to  transfer documents without any problems between my old and new  computers.  BUT....

When I go to FedEx Office (formerly Kinko's)  their copy machines cannot read any files on my memory stick.  My  girlfriend has a windows machine and I've seen her do it, so I suspect  it is an OS compatibility problem.  I've tried reformatting the memory  stick with my Mac, but it still didn't work.  I am trying to open pdf  files, so I don't think that could be the problem.  The guy at OfficeMax  couldn't even call up the files on his computer, but there is one FedEx  Office with particularly good service reps where they can call up and  print my files from their computers.  I'd really like the convenience of  being able to plug in my memory stick and make copies on my own.  Any  suggestions?

My apologies if this question was asked somewhere  else.  Searching the forums, I only found discussions about booting up  from a memory stick.

Thanks for your help!

---

### Post by amsterdamharu on 2011-02-17
With the usb plugged in could you execute the following command?

```
sudo fdisk -l
```

That should show you the disks, if you only have one harddisk your usb should be /dev/sdb1
If it is sdb1 can you execute the following command?
```
sudo fdisk /dev/sdb1
```
press p and enter
press q and enter
Can you post the output of that and the output of the fdisk command?

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code]Your pasted stuff&#91;/code]

---

### Post by Grenage on 2011-02-17
> **PeopleUnite said:**
> Hey everyone,

I just recently got a Systems76 laptop with Ubuntu  10.10, my first Linux based machine!  My old computer is a Power PC  Mac.  I have a SanDisk Cruzer memory stick which I have been using to  transfer documents without any problems between my old and new  computers.  BUT....

When I go to FedEx Office (formerly Kinko's)  their copy machines cannot read any files on my memory stick.  My  girlfriend has a windows machine and I've seen her do it, so I suspect  it is an OS compatibility problem.  I've tried reformatting the memory  stick with my Mac, but it still didn't work.  I am trying to open pdf  files, so I don't think that could be the problem.  The guy at OfficeMax  couldn't even call up the files on his computer, but there is one FedEx  Office with particularly good service reps where they can call up and  print my files from their computers.  I'd really like the convenience of  being able to plug in my memory stick and make copies on my own.  Any  suggestions?

My apologies if this question was asked somewhere  else.  Searching the forums, I only found discussions about booting up  from a memory stick.

Thanks for your help!

For maximum compatibility, format the USB drive using FAT32.  You won't be able to transfer files 4GB or larger.

For decent compatibility, use NTS; you will be able to transfer files 4GB or larger.

---

