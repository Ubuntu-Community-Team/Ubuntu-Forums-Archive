---
title: "partitioning"
date: 2011-04-12
forum: Hardware
---

### Post by p4ndepravity on 2011-04-12
Hello Linux community, this is my first post. I am very excited to finally have worked up the courage to try booting ubuntu. I enjoy challenges so I chose to run ubuntu server cli to start out. This also satisfies my minimalistic outlook. The tipping point for me was windows automatic update, and other app updates, constantly causing my computer to restart and killing my Minecraft server, vnc server, etc. 

So far I have successfully copied my MC server folder into my new linux OS via dvd and started it, setup openssh to op the server from my laptop/iphone, installed and setup webmin. In the future i hope to install a gui and wine so I can run my steam client to play games through steam, but I want to get a good grasp on the cli before I set up a gui. 

I apologize for the lengthy first post, but my excitement abounds (unfortunately my wife doesn't share the sentiment, she hasn't gotten much attention lately =\ )

Now to my actual question. I'm sure its a little late, but I have been reading about partitioning and the benefits of having multiple partitions as opposed to 1 big partition. I currently have 1x200GB sata, 1x80GB ide, and 1x80GB usb-external. I was going to list my partitions and what they're mounted to, but I'd rather just describe my intentions and hopefully someone experienced can describe a scheme that best suits me needs. Since I already installed and mounted my partitions, I guess i'll have to completely redo everything, but I think my server regs own't mind a bit of downtime.

Thanks ahead of time for your help

Here's what I want to do:
I would like to have my Minecraft server on its own partition with the minimum filesystem so I can keep it running in the even of a linux upgrade or another partition locks up or overloads. This will require ~5GB for the server files plus whatever the filesystem will need

I would like to have 20GB for a windows 7 install that can share files (specifically the minecraft server) with the linux system and use grub to dual boot

I would like ~80GB for my music/movies

I would like to have a partition solely for storing a backup image of my linux filesystem (read-only or archived or whatever)

I would like 30-40GB for my steam client and the games that are accessed through steam

Other than that I don't know the ins and outs of the linux filesystem, so i don't know how to partition for the system/app files so i'll probably go with whoever has the scheme that sounds the easiest to configure

again i apologize for the long-winded post, but I'm jazzed about linux and the impressive consistency i've already experienced while administrating my server. Any help or suggestions would be greatly appreciated

---

