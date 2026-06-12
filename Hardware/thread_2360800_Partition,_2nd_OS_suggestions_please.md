---
title: "Partition, 2nd OS suggestions please"
date: 2017-05-08
forum: Hardware
---

### Post by Eagle Nest on 2017-05-08
I have removed another Operating System from the Hard Drive leaving me with 87.5 GiB to play with on a 149 GiB Toshiba Satellite laptop. I am probably just going to leave the Toshiba System Volume and Recovery partitions alone. 

Here is the screenshot from GParted. 

[http://i614.photobucket.com/albums/tt227/Eagle_Nest/screenshot_GParted_and_about.png](http://i614.photobucket.com/albums/tt227/Eagle_Nest/screenshot_GParted_and_about.png)

1. I'd like to create **a data partition **(advice/instruction welcome or link to same) ...

2. but I am also thinking ahead a little. I could **install a 2nd Linux OS** into the unallocated space, something that demands fewer resources, and thereby prolonging the life of the laptop when I would need to upgrade to an Ubuntu OS that requires more than what I have (1.8 GiB RAM, 2x 2 GiB - dual core) in a few years time.  

**Which OS would be a good 2nd for this laptop?** Lubuntu? Xubuntu? Mint? I should mention that, other than pedestrian uses (e mail, browser, music, text and pdf) I use chess applications (ChessBase, Babaschess, Vega, etc.) and I would like to continue to rely upon some version of Linux as my OS while using them. [My next quest is to get ChessBase and Babaschess running under Wine, but one problem at a time!] 

3. I have a 1 TB Seagate Backup Drive as well which I find handy as I use several devices in the household and elsewhere, accessing large chess databases, etc..

---

### Post by RobGoss on 2017-05-08
Hello and welcome, Lubuntu would be my choice it requires less resources and is pretty fast, you can just use the un-allocated space for your new installation. 87.57 GB would be a good amount of disk space if will be using Lubuntu on a daily bases

---

### Post by wildmanne39 on 2017-05-08
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by howefield on 2017-05-09
> **Eagle Nest said:**
> 1. I'd like to create **a data partition **(advice/instruction welcome or link to same) ...

Looks like you would create an Extended partition and then 2 logical partitons within it. One for the new linux installation and one for Data. Mount the Data partition during installation of the new system to have it automatically available.

> Which OS would be a good 2nd for this laptop? Lubuntu? Xubuntu? Mint? I should mention that, other than pedestrian uses (e mail, browser, music, text and pdf) I use chess applications (ChessBase, Babaschess, Vega, etc.) and I would like to continue to rely upon some version of Linux as my OS while using them. [My next quest is to get ChessBase and Babaschess running under Wine, but one problem at a time!]

I'd sugggest giving Xubuntu a try as the best bang for buck in terms of usability and lightness. Chessbase has pretty variable but mostly poor ratings on the Wine website so you might not have a lot of luck with that one but BabasChess should run very well. Haven't a clue what Vega is.

---

### Post by Eagle Nest on 2017-05-10
Thanks, will do. 

Just navigating that Photobucket image hosting site made my browser slow to a crawl. Any alternative suggestions?

---

### Post by Eagle Nest on 2017-05-10
> **howefield said:**
> Looks like you would create an Extended partition and then 2 logical partitons within it. One for the new linux installation and one for Data. Mount the Data partition during installation of the new system to have it automatically available.



I'd sugggest giving Xubuntu a try as the best bang for buck in terms of usability and lightness. Chessbase has pretty variable but mostly poor ratings on the Wine website so you might not have a lot of luck with that one but BabasChess should run very well. Haven't a clue what Vega is.


Thanks for the tips. fyi - Vega is software for chess tournament directors, approved by FIDE, and usable on a Linux platform.

eta/supplemental: I will have a look at the Wine site and the ratings that you mentioned. I read somewhere else that older versions of software, like ChessBase, tend to work better than more recent versions (either under Wine or some other manner I forget at the moment). And I have both a new and an older version of ChessBase, so ...

---

