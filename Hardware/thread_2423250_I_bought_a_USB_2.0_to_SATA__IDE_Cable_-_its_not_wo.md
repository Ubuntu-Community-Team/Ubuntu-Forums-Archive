---
title: "I bought a USB 2.0 to SATA / IDE Cable - its not working"
date: 2019-07-19
forum: Hardware
---

### Post by odyssevs2 on 2019-07-19
I bought a USB 2.0 to SATA / IDE Cable and its not working. I have no idea how to make it work. The drivers that followed are in a cd, and work for only windows and old mac. (From Windows 98 to Windows XP.)

I have two IDE harddrives that I want to get files out of.

Can anyone help me? How do I make this work for ubuntu 18.04? When I ordered the equipment, I was using windows 10. But now I don't have windows 10 anymore, and I'm not sure if I would have made it work for Windows 10 either.

[IMG]https://by3301files.storage.live.com/y4pzc76ovRM6vAXJZx25-GSWhIVn7engLAWw0szu6PCvFkO7kky_VR78DMIMMS0Gwo2mMtSHGXvCejkc2aw1kLCmhSwVG560AVgYbqlZLE_EPc_DiHtz8KXa0Zd7YoNhlHckzCfnZhx5Vvclbp9g50Aq9N6XHvy2QeQYA0eS1OU3q3_dYemy05SeW8II-DjwBaQ/20190719_150515.jpg?psid=1&width=731&height=548[/IMG]

[IMG]https://by3301files.storage.live.com/y4pSTlRUSn-oGd1nC7-FzUw1vkj_RKvE25h15yH3pRRVABc-07nxEotJGmnKAqV9zGTcyy6ZaImPINriIS_cxPIFL4vPEyhvIIVPxUHF0oipp322Gic6DRROmgoi6bBYRC2hlz9UrlVqhNsl01ZlhM4r0-gP0WUps29VVoJ1zaOVzWZINI8gEbMSnuKkFyYmNWN/20190719_150521.jpg?psid=1&width=731&height=548[/IMG]

---

### Post by Autodave on 2019-07-19
Drivers for a cable?  I have an old cable here that simply plugs onto the drive and into a USB slot: it works fine.  Have you tried a different USB port?  I would try that first.

When you connect it to your machine, do you see any icon appear?

Were these drives used on a Win10 machine?  If so, they may be locked due to Windows *fastboot.  *You* may* be able to unlock them by connecting them to a Win10 machine, disabling *fatsboot* and then shutting down the machine completely.

Can you give us the name and model of the cable that you purchased?

---

### Post by TheFu on 2019-07-19
Some of those devices aren't compatible with Linux.

---

### Post by Dennis N on 2019-07-19
These adapters are nice to have around if you have a bare drive you need to access. The adapter I've had for several years is CablesToGo 30504. IDE or SATA. And no driver needed.

---

### Post by ajgreeny on 2019-07-19
This may seem like a silly question but have you thought about the need for the power supply to the SATA/IDE disk you're having problems with?

I have a similar sounding cable setup which I've used for both SATA and IDE disks without any difficulty but I have found it necessary to set up the power supply first and only then insert the USB cable into a port; doing it the other way round does not appear to detect the disk for some unknown (to me, anyway) reason.

---

### Post by oldfred on 2019-07-19
I have a simple USB to SATA cable that uses USB power. No separate power supply. 
Works great for an old SSD. But tried an old HDD and not enough power to spin up HDD.

Does your adapter have separate power supply or only use USB power?

---

### Post by odyssevs2 on 2019-07-19
It only says USB 2.0 to SATA/IDE cable. Made in China. Maybe I bought some useless trash.. :/

It doesnt have a name and model. I tried plugging it into a windows 10 laptop. Nothing happened then either.

---

### Post by odyssevs2 on 2019-07-19
It has a seperate power supply. I plugged it into powersupply on the wall and on USB on the computer. I tried the cable on a windows 10 laptop too. Nothing happened there either..

---

### Post by SeijiSensei on 2019-07-19
I have one of these. Worked flawlessly with Linux the half-dozen times I've needed it.

[https://www.newegg.com/vantec-cb-isatau2-usb-to-ide-sata/p/N82E16812232002?Item=N82E16812232002](https://www.newegg.com/vantec-cb-isatau2-usb-to-ide-sata/p/N82E16812232002?Item=N82E16812232002)

Stupid question time: You aren't accidentally plugging it into a USB 3 port?  Did you try all the ports on the machine?

---

### Post by odyssevs2 on 2019-07-19
Yes. I did try most of the USB ports. Not all of them, there are so many.

You think this is any good?:

[https://www.ebay.co.uk/itm/USB-3-0-to-IDE-SATA-External-Hard-Disk-Converter-3-5-2-5-Hard-Drive-Adapter/192934510597?hash=item2cebcb0005&_trkparms=ispr%3D1&enc=AQAEAAADAKvsXIZtBqdkfsZsMtzFbFsbX3WcW5fmB%2Fx7ZbaZTyexIuMVCyFRE7eVuxoPJPCHMlbGXLC%2BjpJcB8d4cD%2B%2FOXXtXBJlWG%2BArE7o%2FlVHFTykXaXQ8jbLeLy4woVGW5qgOYW%2Bzxz6k7x9oNjFtmDdEhzqfBtBE55Neev4l8L0Z%2FgiCcxt33ojTmeQSM7vTa3Q3UMbjOlmiNtCLlEIO8zsY0GjcgaRzF7eyKvWotF2p2SR%2BMdzOXPX4fQ9DztkqxEnget9b%2FpNxHyoVmPV%2FO%2BqvjTk8A%2Byno3emf22FYw%2FrkySGJSMTAVOxhHcmkh7cu%2F6mjreWRyEx0VVerrQLZJJrf46hoH1LWPCqYGy2VUv6VS5ooFiSB1359NU0bBnjv0kY%2BZoaBbRyEom6CCvArXIuriu0ZK%2B7WPde3goRxmymZpwcrMY6TRdWfnRLHys7P%2F7udWQ%2B92MumAGzE6lMswmWH3vC3teJUjbgYzgukaX8ErsIza8gZTFfcAa7BL1MnMpWBPIVLfkix5ReGxlNOFvbXa2Wo4OSA0ApxCfcunGSgtuOOz237V%2FCjY7elkHJXz9oCnqY70EZt6CyABPDtJjtFnqsqBTtzPrpmgk5OCYihepZyms8qNGNyO3ueYlG8ozXagTdFSWU1kXT3H5EyvZHaQudSPrO%2BghPa%2BU2zyuALhJk34MifTUGsb2aSCRMGmetw5nuukWJf7PScAzLcuIDnfy49GKum9%2BQ%2F47ZhWYMu0wQDAX0pwrNCHYD7Gqqhjk4qHe3ZS1npIdlKSmye1Rn0JZ9xocCOfgniK47Bcz08QSmGI5mzU9YDZbolUkrX3urzcUt%2BPP%2F0e7hD3pcaXi7g8cpGHLh8g702E7dn9b7JGbKfKhCV8Ia88Z8o4ywdk8DRZPOBtlH5MjXAO0hJ%2F1%2F%2BDp8%2BjICqAyFYUK5e%2FyNkeYgsuc1Qp5jHOa0We9%2FHIPq3BsoilsvPtW61NXzObhbif7tgs7Ph1eGvA27%2FnNYI3xgpjEIhQN2eDeyuDqZWNv8g%3D%3D&checksum=192934510597cc75d3d1a8ca4ddda53bc5dc8f4c2329](https://www.ebay.co.uk/itm/USB-3-0-to-IDE-SATA-External-Hard-Disk-Converter-3-5-2-5-Hard-Drive-Adapter/192934510597?hash=item2cebcb0005&_trkparms=ispr%3D1&enc=AQAEAAADAKvsXIZtBqdkfsZsMtzFbFsbX3WcW5fmB%2Fx7ZbaZTyexIuMVCyFRE7eVuxoPJPCHMlbGXLC%2BjpJcB8d4cD%2B%2FOXXtXBJlWG%2BArE7o%2FlVHFTykXaXQ8jbLeLy4woVGW5qgOYW%2Bzxz6k7x9oNjFtmDdEhzqfBtBE55Neev4l8L0Z%2FgiCcxt33ojTmeQSM7vTa3Q3UMbjOlmiNtCLlEIO8zsY0GjcgaRzF7eyKvWotF2p2SR%2BMdzOXPX4fQ9DztkqxEnget9b%2FpNxHyoVmPV%2FO%2BqvjTk8A%2Byno3emf22FYw%2FrkySGJSMTAVOxhHcmkh7cu%2F6mjreWRyEx0VVerrQLZJJrf46hoH1LWPCqYGy2VUv6VS5ooFiSB1359NU0bBnjv0kY%2BZoaBbRyEom6CCvArXIuriu0ZK%2B7WPde3goRxmymZpwcrMY6TRdWfnRLHys7P%2F7udWQ%2B92MumAGzE6lMswmWH3vC3teJUjbgYzgukaX8ErsIza8gZTFfcAa7BL1MnMpWBPIVLfkix5ReGxlNOFvbXa2Wo4OSA0ApxCfcunGSgtuOOz237V%2FCjY7elkHJXz9oCnqY70EZt6CyABPDtJjtFnqsqBTtzPrpmgk5OCYihepZyms8qNGNyO3ueYlG8ozXagTdFSWU1kXT3H5EyvZHaQudSPrO%2BghPa%2BU2zyuALhJk34MifTUGsb2aSCRMGmetw5nuukWJf7PScAzLcuIDnfy49GKum9%2BQ%2F47ZhWYMu0wQDAX0pwrNCHYD7Gqqhjk4qHe3ZS1npIdlKSmye1Rn0JZ9xocCOfgniK47Bcz08QSmGI5mzU9YDZbolUkrX3urzcUt%2BPP%2F0e7hD3pcaXi7g8cpGHLh8g702E7dn9b7JGbKfKhCV8Ia88Z8o4ywdk8DRZPOBtlH5MjXAO0hJ%2F1%2F%2BDp8%2BjICqAyFYUK5e%2FyNkeYgsuc1Qp5jHOa0We9%2FHIPq3BsoilsvPtW61NXzObhbif7tgs7Ph1eGvA27%2FnNYI3xgpjEIhQN2eDeyuDqZWNv8g%3D%3D&checksum=192934510597cc75d3d1a8ca4ddda53bc5dc8f4c2329)

---

### Post by SeijiSensei on 2019-07-20
I really cannot judge whether another device will work properly or not. I will mention that there is a USB 3.0 version of the device I cited above:  [https://www.newegg.com/vantec-cb-isa225-u3-usb-to-ide-sata/p/N82E16812232064?Item=N82E16812232064](https://www.newegg.com/vantec-cb-isa225-u3-usb-to-ide-sata/p/N82E16812232064?Item=N82E16812232064)

---

