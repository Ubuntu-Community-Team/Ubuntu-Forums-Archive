---
title: "Building LAN server for printers and hosting files"
date: 2008-07-21
forum: General Help
---

### Post by MaxIBoy on 2008-07-21
Here's the parts list I've come up with:
[https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=8055491](https://secure.newegg.com/WishList/MySavedWishDetail.aspx?ID=8055491)

Can you think of anything I'm missing here? The server will have three printers (one of which will be thrown out when it runs out of ink; we're running it into the ground because it's too old.) It will also be used to move files around, possibly even to access files over the Internet.

Also, my dad wants proof that this will work if the server is on our LAN alongside our two other computers. The LAN consists of a four-port hub.


```
Wish list details
server

Qty. 	Image 	Product Description 	Unit Price 	Savings 	Total Price 
1 	Linkworld PRESCOTT 43701-222FU Black SECC/SGCC MicroATX Mid Tower Computer Case 	

    Linkworld PRESCOTT 43701-222FU Black SECC/SGCC MicroATX Mid Tower Computer Case - Retail
    Model #:43701-222FU
    Item #:N82E16811164114
    Return Policy:Standard Return Policy
    In Stock

	$22.99 	  	$22.99
1 	ECS Goal3+(1.1C) AMD Sempron 3000+ 754 SiS 761 GX Micro ATX Motherboard/CPU Combo 	

    ECS Goal3+(1.1C) AMD Sempron 3000+ 754 SiS 761 GX Micro ATX Motherboard/CPU Combo - Retail
    Model #:Goal3+(1.1C)
    Item #:N82E16813135060
    Return Policy:Limited 30-Day Return Policy
    In Stock
    Mail-in Rebate

	$59.99 	-$10.00 Instant 	$49.99
1 	Rosewill RV300 300W ATX12V Power Supply 	

    Rosewill RV300 300W ATX12V Power Supply - Retail
    Model #:RV300
    Item #:N82E16817182001
    Return Policy:Standard Return Policy
    In Stock

	$15.99 	-$3.00 Instant 	$12.99
1 	Kingston ValueRAM 256MB 184-Pin DDR SDRAM DDR 400 (PC 3200) System Memory Model KVR400X64C25/256 	

    Kingston ValueRAM 256MB 184-Pin DDR SDRAM DDR 400 (PC 3200) System Memory Model KVR400X64C25/256 - Retail
    Model #:KVR400X64C25/256
    Item #:N82E16820141401
    Return Policy:Memory (Modules, USB) Return Policy
    In Stock

	$12.99 	  	$12.99
1 	EXCELSTOR Jupiter Series ESJ8080S 80GB 7200 RPM SATA 3.0Gb/s Hard Drive 	

    EXCELSTOR Jupiter Series ESJ8080S 80GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM
    Model #:ESJ8080S
    Item #:N82E16822210003
    Return Policy:Limited 30-Day Return Policy
    In Stock

	$34.99 	  	$34.99
1 	MASSCOOL 5F9001B1H3 80mm Ball CPU Cooler 	

    MASSCOOL 5F9001B1H3 80mm Ball CPU Cooler - Retail
    Model #:5F9001B1H3
    Item #:N82E16835150087
    Return Policy:Standard Return Policy
    In Stock

	$9.99 	  	$9.99
Subtotal: 	$143.94
```

---

### Post by Potatoj316 on 2008-07-21
It should be able to share file without a problem on your LAN, as long as you have all the necessary packages for sharing files (samba)  If you want to share files over the internet I sugest you install apache.  You will then need to set your router to forword port 80 (the default internet port) to the IP address of the server.  I dont know about your ISP but mine blocks port 80 incoming requests so I had to change the port, you can do this in one of the apache config files (i dont remember which)

---

### Post by MaxIBoy on 2008-07-21
Thank you. *Shows to dad.*



What is your ISP? Is it Comcast? My ISP is Comcast, I want to know if it's likely to block port 80 requests.

---

### Post by Potatoj316 on 2008-07-21
It probably will block port 80, I think most do, it is to discourage hosting websites from home computers without paying extra for a static IP.  Oh, and another thing your IP is probably dynamic (it changes) as long as you have a computer connected to the internet it shoulnt change though.  (mine hasnt changed in over a year, but if I turn all my computers off it does)  You can then get a free subdomain from dyndns.org.  

You can tell apache to host on multiple ports if you want.  Do a quick search on google for "apache port linux" (or something like that) and you will find what you need

---

### Post by MaxIBoy on 2008-07-21
Thank you, I will do that.

---

