---
title: "Sony Memory Stick/Card..."
date: 2009-07-08
forum: Hardware
---

### Post by Kaneda187 on 2009-07-08
I have a card reader integrated into my laptop but It wont read the card from my camera, Its a Sony Magic Gate card..... Its strange because it will read a normal SD card but will not read the magic gate kind...

Any Ideas?
Thanx!

---

### Post by adam_kimber on 2009-07-08
Hi. Magicgate is an encryption chip on Sony Memory Sticks. Unfortunately these are not the same as standard SD cards and your reader will have to be able to accept Memory Sticks. If the laptop and card reader are fairly old they might not have [Magicgate]("http://en.wikipedia.org/wiki/MagicGate") built in. Both card and reader need Magicgate in them for the encryption/decryption to work.

However if the above is not the case then I expect Sony has struck again. A lot of Sony products do not adhere to the standards and therefore require some work-around to get them to work in Ubuntu. 

Can you please post the output of the last ten lines of dmesg (either type that in a terminal or go to system log and click on messages) after you put the card in the reader.

---

### Post by Kaneda187 on 2009-07-08
the card works if i boot into windows but im not too fond of doing that. 

heres the output:
```
[12968.271214] vc032x: Unknown sensor...
[12968.271242] vc032x: probe of 1-8:1.0 failed with error -22
[12968.271548] usb 1-8: USB disconnect, address 37
[12968.540081] usb 1-8: new high speed USB device using ehci_hcd and address 38
[12968.696421] usb 1-8: configuration #1 chosen from 1 choice
[12968.696790] gspca: probing 046d:0892
[12968.905507] vc032x: check sensor header 44
[12968.907582] vc032x: I2c Bus Busy Wait 0
[12968.910835] vc032x: I2c Bus Busy Wait 0
[12968.912827] vc032x: I2c Bus Busy Wait 0
[12968.914823] vc032x: I2c Bus Busy Wait 0
[12968.916827] vc032x: I2c Bus Busy Wait 0
[12968.918828] vc032x: I2c Bus Busy Wait 0
[12968.918833] vc032x: Unknown sensor...
[12968.918864] vc032x: probe of 1-8:1.0 failed with error -22
[12968.921735] usb 1-8: USB disconnect, address 38
[12969.192111] usb 1-8: new high speed USB device using ehci_hcd and address 39
[12969.348500] usb 1-8: configuration #1 chosen from 1 choice
[12969.348881] gspca: probing 046d:0892
[12969.556509] vc032x: check sensor header 44
[12969.558582] vc032x: I2c Bus Busy Wait 0
[12969.560960] vc032x: I2c Bus Busy Wait 0
[12969.562947] vc032x: I2c Bus Busy Wait 0
[12969.565325] vc032x: I2c Bus Busy Wait 0
[12969.567326] vc032x: I2c Bus Busy Wait 0
[12969.569579] vc032x: I2c Bus Busy Wait 0
[12969.569584] vc032x: Unknown sensor...
[12969.569613] vc032x: probe of 1-8:1.0 failed with error -22
[12969.569921] usb 1-8: USB disconnect, address 39
[12969.840128] usb 1-8: new high speed USB device using ehci_hcd and address 40
[12969.997631] usb 1-8: configuration #1 chosen from 1 choice
[12969.998022] gspca: probing 046d:0892
[12970.208480] vc032x: check sensor header 44
[12970.210581] vc032x: I2c Bus Busy Wait 0
[12970.212950] vc032x: I2c Bus Busy Wait 0
[12970.215582] vc032x: I2c Bus Busy Wait 0
[12970.217958] vc032x: I2c Bus Busy Wait 0
[12970.221105] vc032x: I2c Bus Busy Wait 0
[12970.223075] vc032x: I2c Bus Busy Wait 0
[12970.223080] vc032x: Unknown sensor...
[12970.223111] vc032x: probe of 1-8:1.0 failed with error -22
[12970.223418] usb 1-8: USB disconnect, address 40
[12970.492114] usb 1-8: new high speed USB device using ehci_hcd and address 41
[12970.648394] usb 1-8: configuration #1 chosen from 1 choice
[12970.648761] gspca: probing 046d:0892
[12970.856510] vc032x: check sensor header 44
[12970.858882] vc032x: I2c Bus Busy Wait 0
[12970.861445] vc032x: I2c Bus Busy Wait 0
[12970.863444] vc032x: I2c Bus Busy Wait 0
[12970.866853] vc032x: I2c Bus Busy Wait 0
[12970.868839] vc032x: I2c Bus Busy Wait 0
[12970.871093] vc032x: I2c Bus Busy Wait 0
[12970.871097] vc032x: Unknown sensor...
[12970.871126] vc032x: probe of 1-8:1.0 failed with error -22
[12970.874052] usb 1-8: USB disconnect, address 41
[12971.145105] usb 1-8: new high speed USB device using ehci_hcd and address 42
[12971.301310] usb 1-8: configuration #1 chosen from 1 choice
[12971.301780] gspca: probing 046d:0892
[12971.520480] vc032x: check sensor header 44
[12971.522575] vc032x: I2c Bus Busy Wait 0
[12971.524581] vc032x: I2c Bus Busy Wait 0
[12971.526583] vc032x: I2c Bus Busy Wait 0
[12971.528709] vc032x: I2c Bus Busy Wait 0
[12971.531074] vc032x: I2c Bus Busy Wait 0
[12971.533337] vc032x: I2c Bus Busy Wait 0
[12971.533343] vc032x: Unknown sensor...
[12971.533374] vc032x: probe of 1-8:1.0 failed with error -22
[12971.533684] usb 1-8: USB disconnect, address 42
[12971.804119] usb 1-8: new high speed USB device using ehci_hcd and address 43
[12971.961221] usb 1-8: configuration #1 chosen from 1 choice
[12971.961638] gspca: probing 046d:0892
[12972.180509] vc032x: check sensor header 44
[12972.182582] vc032x: I2c Bus Busy Wait 0
[12972.184961] vc032x: I2c Bus Busy Wait 0
[12972.187200] vc032x: I2c Bus Busy Wait 0
[12972.189460] vc032x: I2c Bus Busy Wait 0
[12972.191952] vc032x: I2c Bus Busy Wait 0
[12972.194211] vc032x: I2c Bus Busy Wait 0
[12972.194217] vc032x: Unknown sensor...
[12972.194248] vc032x: probe of 1-8:1.0 failed with error -22
[12972.194558] usb 1-8: USB disconnect, address 43
[12972.464079] usb 1-8: new high speed USB device using ehci_hcd and address 44
[12972.620546] usb 1-8: configuration #1 chosen from 1 choice
[12972.633646] gspca: probing 046d:0892
[12972.841230] vc032x: check sensor header 44
[12972.843326] vc032x: I2c Bus Busy Wait 0
[12972.845333] vc032x: I2c Bus Busy Wait 0
[12972.847331] vc032x: I2c Bus Busy Wait 0
[12972.849458] vc032x: I2c Bus Busy Wait 0
[12972.851449] vc032x: I2c Bus Busy Wait 0
[12972.853589] vc032x: I2c Bus Busy Wait 0
[12972.853595] vc032x: Unknown sensor...
[12972.853627] vc032x: probe of 1-8:1.0 failed with error -22
[12972.853943] usb 1-8: USB disconnect, address 44
[12973.124138] usb 1-8: new high speed USB device using ehci_hcd and address 45
[12973.280261] usb 1-8: configuration #1 chosen from 1 choice
[12973.280634] gspca: probing 046d:0892
[12973.488510] vc032x: check sensor header 44
[12973.490578] vc032x: I2c Bus Busy Wait 0
[12973.493335] vc032x: I2c Bus Busy Wait 0
[12973.495330] vc032x: I2c Bus Busy Wait 0
[12973.497710] vc032x: I2c Bus Busy Wait 0
[12973.499703] vc032x: I2c Bus Busy Wait 0
[12973.502714] vc032x: I2c Bus Busy Wait 0
[12973.502720] vc032x: Unknown sensor...
[12973.502750] vc032x: probe of 1-8:1.0 failed with error -22
[12973.503077] usb 1-8: USB disconnect, address 45
[12973.772069] usb 1-8: new high speed USB device using ehci_hcd and address 46
[12973.928300] usb 1-8: configuration #1 chosen from 1 choice
[12973.928669] gspca: probing 046d:0892
[12974.136506] vc032x: check sensor header 44
[12974.138599] vc032x: I2c Bus Busy Wait 0
[12974.140960] vc032x: I2c Bus Busy Wait 0
[12974.142957] vc032x: I2c Bus Busy Wait 0
[12974.145080] vc032x: I2c Bus Busy Wait 0
[12974.147076] vc032x: I2c Bus Busy Wait 0
[12974.149334] vc032x: I2c Bus Busy Wait 0
[12974.149339] vc032x: Unknown sensor...
[12974.149368] vc032x: probe of 1-8:1.0 failed with error -22
[12974.149676] usb 1-8: USB disconnect, address 46
[12974.420134] usb 1-8: new high speed USB device using ehci_hcd and address 47
[12974.576551] usb 1-8: configuration #1 chosen from 1 choice
[12974.576917] gspca: probing 046d:0892
[12974.784509] vc032x: check sensor header 44
[12974.786582] vc032x: I2c Bus Busy Wait 0
[12974.789227] vc032x: I2c Bus Busy Wait 0
[12974.791830] vc032x: I2c Bus Busy Wait 0
[12974.794212] vc032x: I2c Bus Busy Wait 0
[12974.796320] vc032x: I2c Bus Busy Wait 0
[12974.798334] vc032x: I2c Bus Busy Wait 0
[12974.798339] vc032x: Unknown sensor...
[12974.798368] vc032x: probe of 1-8:1.0 failed with error -22
[12974.798674] usb 1-8: USB disconnect, address 47
[12975.068085] usb 1-8: new high speed USB device using ehci_hcd and address 48
[12975.224394] usb 1-8: configuration #1 chosen from 1 choice
[12975.224775] gspca: probing 046d:0892
[12975.432508] vc032x: check sensor header 44
[12975.434583] vc032x: I2c Bus Busy Wait 0
[12975.436960] vc032x: I2c Bus Busy Wait 0
[12975.438957] vc032x: I2c Bus Busy Wait 0
[12975.441476] vc032x: I2c Bus Busy Wait 0
[12975.443463] vc032x: I2c Bus Busy Wait 0
[12975.445726] vc032x: I2c Bus Busy Wait 0
[12975.445731] vc032x: Unknown sensor...
[12975.445760] vc032x: probe of 1-8:1.0 failed with error -22
[12975.446060] usb 1-8: USB disconnect, address 48
[12975.716151] usb 1-8: new high speed USB device using ehci_hcd and address 49
[12975.872518] usb 1-8: configuration #1 chosen from 1 choice
[12975.872907] gspca: probing 046d:0892
[12976.080509] vc032x: check sensor header 44
[12976.082582] vc032x: I2c Bus Busy Wait 0
[12976.084710] vc032x: I2c Bus Busy Wait 0
[12976.086708] vc032x: I2c Bus Busy Wait 0
[12976.088960] vc032x: I2c Bus Busy Wait 0
[12976.091503] vc032x: I2c Bus Busy Wait 0
[12976.093456] vc032x: I2c Bus Busy Wait 0
[12976.093461] vc032x: Unknown sensor...
[12976.093489] vc032x: probe of 1-8:1.0 failed with error -22
[12976.093796] usb 1-8: USB disconnect, address 49
[12976.364116] usb 1-8: new high speed USB device using ehci_hcd and address 50
[12976.520389] usb 1-8: configuration #1 chosen from 1 choice
[12976.520763] gspca: probing 046d:0892
[12976.733507] vc032x: check sensor header 44
[12976.735583] vc032x: I2c Bus Busy Wait 0
[12976.737837] vc032x: I2c Bus Busy Wait 0
[12976.739830] vc032x: I2c Bus Busy Wait 0
[12976.742087] vc032x: I2c Bus Busy Wait 0
[12976.744275] vc032x: I2c Bus Busy Wait 0
[12976.746208] vc032x: I2c Bus Busy Wait 0
[12976.746215] vc032x: Unknown sensor...
[12976.746246] vc032x: probe of 1-8:1.0 failed with error -22
[12976.746634] usb 1-8: USB disconnect, address 50
[12977.023044] usb 1-8: new high speed USB device using ehci_hcd and address 51
[12977.181922] usb 1-8: configuration #1 chosen from 1 choice
[12977.182293] gspca: probing 046d:0892
[12977.388605] vc032x: check sensor header 44
[12977.391207] vc032x: I2c Bus Busy Wait 0
[12977.393081] vc032x: I2c Bus Busy Wait 0
[12977.395208] vc032x: I2c Bus Busy Wait 0
[12977.397334] vc032x: I2c Bus Busy Wait 0
[12977.399332] vc032x: I2c Bus Busy Wait 0
[12977.401996] vc032x: I2c Bus Busy Wait 0
[12977.402001] vc032x: Unknown sensor...
[12977.402029] vc032x: probe of 1-8:1.0 failed with error -22
[12977.402330] usb 1-8: USB disconnect, address 51
[12977.672070] usb 1-8: new high speed USB device using ehci_hcd and address 52
[12977.828296] usb 1-8: configuration #1 chosen from 1 choice
[12977.828662] gspca: probing 046d:0892
[12978.036508] vc032x: check sensor header 44
[12978.038578] vc032x: I2c Bus Busy Wait 0
[12978.040943] vc032x: I2c Bus Busy Wait 0
[12978.043196] vc032x: I2c Bus Busy Wait 0
[12978.045459] vc032x: I2c Bus Busy Wait 0
[12978.047453] vc032x: I2c Bus Busy Wait 0
[12978.049581] vc032x: I2c Bus Busy Wait 0
[12978.049586] vc032x: Unknown sensor...
[12978.049614] vc032x: probe of 1-8:1.0 failed with error -22
[12978.049923] usb 1-8: USB disconnect, address 52
[12978.320102] usb 1-8: new high speed USB device using ehci_hcd and address 53
[12978.478641] usb 1-8: configuration #1 chosen from 1 choice
[12978.479032] gspca: probing 046d:0892
[12978.688509] vc032x: check sensor header 44
[12978.690583] vc032x: I2c Bus Busy Wait 0
[12978.692961] vc032x: I2c Bus Busy Wait 0
[12978.694957] vc032x: I2c Bus Busy Wait 0
[12978.697086] vc032x: I2c Bus Busy Wait 0
[12978.699082] vc032x: I2c Bus Busy Wait 0
[12978.701335] vc032x: I2c Bus Busy Wait 0
[12978.701340] vc032x: Unknown sensor...
[12978.701368] vc032x: probe of 1-8:1.0 failed with error -22
[12978.703834] usb 1-8: USB disconnect, address 53
[12978.977099] usb 1-8: new high speed USB device using ehci_hcd and address 54
[12979.132375] usb 1-8: configuration #1 chosen from 1 choice
[12979.132863] gspca: probing 046d:0892
[12979.340464] vc032x: check sensor header 44
[12979.342580] vc032x: I2c Bus Busy Wait 0
[12979.344962] vc032x: I2c Bus Busy Wait 0
[12979.346952] vc032x: I2c Bus Busy Wait 0
[12979.349086] vc032x: I2c Bus Busy Wait 0
[12979.351080] vc032x: I2c Bus Busy Wait 0
[12979.353337] vc032x: I2c Bus Busy Wait 0
[12979.353342] vc032x: Unknown sensor...
[12979.353370] vc032x: probe of 1-8:1.0 failed with error -22
[12979.353682] usb 1-8: USB disconnect, address 54
[12979.625109] usb 1-8: new high speed USB device using ehci_hcd and address 55
[12979.780420] usb 1-8: configuration #1 chosen from 1 choice
[12979.780786] gspca: probing 046d:0892
[12979.988504] vc032x: check sensor header 44
[12979.990583] vc032x: I2c Bus Busy Wait 0
[12979.992737] vc032x: I2c Bus Busy Wait 0
[12979.994708] vc032x: I2c Bus Busy Wait 0
[12979.996831] vc032x: I2c Bus Busy Wait 0
[12979.998837] vc032x: I2c Bus Busy Wait 0
[12980.010115] vc032x: I2c Bus Busy Wait 0
[12980.010121] vc032x: Unknown sensor...
[12980.010152] vc032x: probe of 1-8:1.0 failed with error -22
[12980.010458] usb 1-8: USB disconnect, address 55
[12980.249107] usb 1-8: new high speed USB device using ehci_hcd and address 56
[12980.408520] usb 1-8: configuration #1 chosen from 1 choice
[12980.408907] gspca: probing 046d:0892
[12980.616493] vc032x: check sensor header 44
[12980.618584] vc032x: I2c Bus Busy Wait 0
[12980.620961] vc032x: I2c Bus Busy Wait 0
[12980.623458] vc032x: I2c Bus Busy Wait 0
[12980.625586] vc032x: I2c Bus Busy Wait 0
[12980.627583] vc032x: I2c Bus Busy Wait 0
[12980.629833] vc032x: I2c Bus Busy Wait 0
[12980.629838] vc032x: Unknown sensor...
[12980.629866] vc032x: probe of 1-8:1.0 failed with error -22
[12980.630174] usb 1-8: USB disconnect, address 56
[12980.900110] usb 1-8: new high speed USB device using ehci_hcd and address 57
[12981.056423] usb 1-8: configuration #1 chosen from 1 choice
[12981.056788] gspca: probing 046d:0892
[12981.264704] vc032x: check sensor header 44
[12981.267836] vc032x: I2c Bus Busy Wait 0
[12981.269835] vc032x: I2c Bus Busy Wait 0
[12981.271974] vc032x: I2c Bus Busy Wait 0
[12981.274083] vc032x: I2c Bus Busy Wait 0
[12981.276231] vc032x: I2c Bus Busy Wait 0
[12981.278076] vc032x: I2c Bus Busy Wait 0
[12981.278081] vc032x: Unknown sensor...
[12981.278109] vc032x: probe of 1-8:1.0 failed with error -22
[12981.278419] usb 1-8: USB disconnect, address 57
[12981.548069] usb 1-8: new high speed USB device using ehci_hcd and address 58
[12981.704422] usb 1-8: configuration #1 chosen from 1 choice
[12981.704794] gspca: probing 046d:0892
[12981.913100] vc032x: check sensor header 44
[12981.915201] vc032x: I2c Bus Busy Wait 0
[12981.918585] vc032x: I2c Bus Busy Wait 0
[12981.920748] vc032x: I2c Bus Busy Wait 0
[12981.922710] vc032x: I2c Bus Busy Wait 0
[12981.925461] vc032x: I2c Bus Busy Wait 0
[12981.927456] vc032x: I2c Bus Busy Wait 0
[12981.927461] vc032x: Unknown sensor...
[12981.927489] vc032x: probe of 1-8:1.0 failed with error -22
[12981.927796] usb 1-8: USB disconnect, address 58
[12982.201103] usb 1-8: new high speed USB device using ehci_hcd and address 59
[12982.360645] usb 1-8: configuration #1 chosen from 1 choice
[12982.361009] gspca: probing 046d:0892
[12982.568509] vc032x: check sensor header 44
[12982.570586] vc032x: I2c Bus Busy Wait 0
[12982.572707] vc032x: I2c Bus Busy Wait 0
[12982.574707] vc032x: I2c Bus Busy Wait 0
[12982.576847] vc032x: I2c Bus Busy Wait 0
[12982.579084] vc032x: I2c Bus Busy Wait 0
[12982.581337] vc032x: I2c Bus Busy Wait 0
[12982.581342] vc032x: Unknown sensor...
[12982.581372] vc032x: probe of 1-8:1.0 failed with error -22
[12982.581683] usb 1-8: USB disconnect, address 59
[12982.852115] usb 1-8: new high speed USB device using ehci_hcd and address 60
[12983.025862] usb 1-8: configuration #1 chosen from 1 choice
[12983.026314] gspca: probing 046d:0892
[12983.233226] vc032x: check sensor header 44
[12983.235335] vc032x: I2c Bus Busy Wait 0
[12983.237839] vc032x: I2c Bus Busy Wait 0
[12983.239833] vc032x: I2c Bus Busy Wait 0
[12983.242213] vc032x: I2c Bus Busy Wait 0
[12983.244382] vc032x: I2c Bus Busy Wait 0
[12983.246331] vc032x: I2c Bus Busy Wait 0
[12983.246337] vc032x: Unknown sensor...
[12983.246368] vc032x: probe of 1-8:1.0 failed with error -22
[12983.246682] usb 1-8: USB disconnect, address 60
[12983.516116] usb 1-8: new high speed USB device using ehci_hcd and address 61
[12983.673301] usb 1-8: configuration #1 chosen from 1 choice
[12983.673679] gspca: probing 046d:0892
[12983.880510] vc032x: check sensor header 44
[12983.883291] vc032x: I2c Bus Busy Wait 0
[12983.885457] vc032x: I2c Bus Busy Wait 0
[12983.887457] vc032x: I2c Bus Busy Wait 0
[12983.889715] vc032x: I2c Bus Busy Wait 0
[12983.891701] vc032x: I2c Bus Busy Wait 0
[12983.893961] vc032x: I2c Bus Busy Wait 0
[12983.893967] vc032x: Unknown sensor...
[12983.893995] vc032x: probe of 1-8:1.0 failed with error -22
[12983.894304] usb 1-8: USB disconnect, address 61
[12984.164109] usb 1-8: new high speed USB device using ehci_hcd and address 62
[12984.321011] usb 1-8: configuration #1 chosen from 1 choice
[12984.321387] gspca: probing 046d:0892
[12984.528509] vc032x: check sensor header 44
[12984.530585] vc032x: I2c Bus Busy Wait 0
[12984.533464] vc032x: I2c Bus Busy Wait 0
[12984.535456] vc032x: I2c Bus Busy Wait 0
[12984.537713] vc032x: I2c Bus Busy Wait 0
[12984.539708] vc032x: I2c Bus Busy Wait 0
[12984.541962] vc032x: I2c Bus Busy Wait 0
[12984.541967] vc032x: Unknown sensor...
[12984.541995] vc032x: probe of 1-8:1.0 failed with error -22
[12984.542301] usb 1-8: USB disconnect, address 62
[12984.812102] usb 1-8: new high speed USB device using ehci_hcd and address 63
[12984.974024] usb 1-8: configuration #1 chosen from 1 choice
[12984.974385] gspca: probing 046d:0892
[12985.184485] vc032x: check sensor header 44
[12985.186587] vc032x: I2c Bus Busy Wait 0
[12985.189338] vc032x: I2c Bus Busy Wait 0
[12985.191328] vc032x: I2c Bus Busy Wait 0
[12985.193585] vc032x: I2c Bus Busy Wait 0
[12985.195579] vc032x: I2c Bus Busy Wait 0
[12985.197829] vc032x: I2c Bus Busy Wait 0
[12985.197833] vc032x: Unknown sensor...
[12985.197862] vc032x: probe of 1-8:1.0 failed with error -22
[12985.198171] usb 1-8: USB disconnect, address 63
[12985.468086] usb 1-8: new high speed USB device using ehci_hcd and address 64
[12985.624431] usb 1-8: configuration #1 chosen from 1 choice
[12985.624792] gspca: probing 046d:0892
[12985.832510] vc032x: check sensor header 44
[12985.834861] vc032x: I2c Bus Busy Wait 0
[12985.836964] vc032x: I2c Bus Busy Wait 0
[12985.838958] vc032x: I2c Bus Busy Wait 0
[12985.841077] vc032x: I2c Bus Busy Wait 0
[12985.843082] vc032x: I2c Bus Busy Wait 0
[12985.845584] vc032x: I2c Bus Busy Wait 0
[12985.845591] vc032x: Unknown sensor...
[12985.845621] vc032x: probe of 1-8:1.0 failed with error -22
[12985.845929] usb 1-8: USB disconnect, address 64
[12986.116106] usb 1-8: new high speed USB device using ehci_hcd and address 65
[12986.272419] usb 1-8: configuration #1 chosen from 1 choice
[12986.272780] gspca: probing 046d:0892
[12986.483590] vc032x: check sensor header 44
[12986.485827] vc032x: I2c Bus Busy Wait 0
[12986.487831] vc032x: I2c Bus Busy Wait 0
[12986.490214] vc032x: I2c Bus Busy Wait 0
[12986.492413] vc032x: I2c Bus Busy Wait 0
[12986.495063] vc032x: I2c Bus Busy Wait 0
[12986.497213] vc032x: I2c Bus Busy Wait 0
[12986.497219] vc032x: Unknown sensor...
[12986.497248] vc032x: probe of 1-8:1.0 failed with error -22
[12986.500907] usb 1-8: USB disconnect, address 65
[12986.772136] usb 1-8: new high speed USB device using ehci_hcd and address 66
[12986.932301] usb 1-8: configuration #1 chosen from 1 choice
[12986.932667] gspca: probing 046d:0892
[12987.140474] vc032x: check sensor header 44
[12987.142575] vc032x: I2c Bus Busy Wait 0
[12987.144956] vc032x: I2c Bus Busy Wait 0
[12987.146958] vc032x: I2c Bus Busy Wait 0
[12987.149450] vc032x: I2c Bus Busy Wait 0
[12987.151449] vc032x: I2c Bus Busy Wait 0
[12987.153573] vc032x: I2c Bus Busy Wait 0
[12987.153578] vc032x: Unknown sensor...
[12987.153607] vc032x: probe of 1-8:1.0 failed with error -22
[12987.154432] usb 1-8: USB disconnect, address 66
[12987.424076] usb 1-8: new high speed USB device using ehci_hcd and address 67
[12987.582765] usb 1-8: configuration #1 chosen from 1 choice
[12987.583310] gspca: probing 046d:0892
[12987.792464] vc032x: check sensor header 44
[12987.794585] vc032x: I2c Bus Busy Wait 0
[12987.796576] vc032x: I2c Bus Busy Wait 0
[12987.798576] vc032x: I2c Bus Busy Wait 0
[12987.800577] vc032x: I2c Bus Busy Wait 0
[12987.802579] vc032x: I2c Bus Busy Wait 0
[12987.805203] vc032x: I2c Bus Busy Wait 0
[12987.805209] vc032x: Unknown sensor...
[12987.805238] vc032x: probe of 1-8:1.0 failed with error -22
[12987.805552] usb 1-8: USB disconnect, address 67
[12988.076083] usb 1-8: new high speed USB device using ehci_hcd and address 68
[12988.236515] usb 1-8: configuration #1 chosen from 1 choice
[12988.236950] gspca: probing 046d:0892
[12988.446059] vc032x: check sensor header 44
[12988.448440] vc032x: I2c Bus Busy Wait 0
[12988.450339] vc032x: I2c Bus Busy Wait 0
[12988.452719] vc032x: I2c Bus Busy Wait 0
[12988.454709] vc032x: I2c Bus Busy Wait 0
[12988.457087] vc032x: I2c Bus Busy Wait 0
[12988.459209] vc032x: I2c Bus Busy Wait 0
[12988.459214] vc032x: Unknown sensor...
[12988.459248] vc032x: probe of 1-8:1.0 failed with error -22
[12988.459569] usb 1-8: USB disconnect, address 68
[12988.728040] usb 1-8: new high speed USB device using ehci_hcd and address 69
[12988.887337] usb 1-8: configuration #1 chosen from 1 choice
[12988.887897] gspca: probing 046d:0892
[12989.096484] vc032x: check sensor header 44
[12989.098580] vc032x: I2c Bus Busy Wait 0
[12989.100981] vc032x: I2c Bus Busy Wait 0
[12989.102958] vc032x: I2c Bus Busy Wait 0
[12989.105213] vc032x: I2c Bus Busy Wait 0
[12989.107193] vc032x: I2c Bus Busy Wait 0
[12989.110569] vc032x: I2c Bus Busy Wait 0
[12989.110575] vc032x: Unknown sensor...
[12989.110605] vc032x: probe of 1-8:1.0 failed with error -22
[12989.110917] usb 1-8: USB disconnect, address 69
[12989.381124] usb 1-8: new high speed USB device using ehci_hcd and address 70
[12989.540512] usb 1-8: configuration #1 chosen from 1 choice
[12989.540900] gspca: probing 046d:0892
[12989.748465] vc032x: check sensor header 44
[12989.750575] vc032x: I2c Bus Busy Wait 0
[12989.752961] vc032x: I2c Bus Busy Wait 0
[12989.755468] vc032x: I2c Bus Busy Wait 0
[12989.758827] vc032x: I2c Bus Busy Wait 0
[12989.761084] vc032x: I2c Bus Busy Wait 0
[12989.763201] vc032x: I2c Bus Busy Wait 0
[12989.763206] vc032x: Unknown sensor...
[12989.763235] vc032x: probe of 1-8:1.0 failed with error -22
[12989.763543] usb 1-8: USB disconnect, address 70
[12990.037043] usb 1-8: new high speed USB device using ehci_hcd and address 71
[12990.200968] usb 1-8: configuration #1 chosen from 1 choice
[12990.201411] gspca: probing 046d:0892
[12990.425828] vc032x: check sensor header 44
[12990.427943] vc032x: I2c Bus Busy Wait 0
[12990.431511] vc032x: I2c Bus Busy Wait 0
[12990.434211] vc032x: I2c Bus Busy Wait 0
[12990.436212] vc032x: I2c Bus Busy Wait 0
[12990.438460] vc032x: I2c Bus Busy Wait 0
[12990.440460] vc032x: I2c Bus Busy Wait 0
[12990.440464] vc032x: Unknown sensor...
[12990.440495] vc032x: probe of 1-8:1.0 failed with error -22
[12990.440806] usb 1-8: USB disconnect, address 71
[12990.722268] usb 1-8: new high speed USB device using ehci_hcd and address 72
[12990.890687] usb 1-8: configuration #1 chosen from 1 choice
[12990.891168] gspca: probing 046d:0892
[12991.097501] vc032x: check sensor header 44
[12991.099588] vc032x: I2c Bus Busy Wait 0
[12991.101847] vc032x: I2c Bus Busy Wait 0
[12991.103840] vc032x: I2c Bus Busy Wait 0
[12991.105986] vc032x: I2c Bus Busy Wait 0
[12991.107959] vc032x: I2c Bus Busy Wait 0
[12991.110858] vc032x: I2c Bus Busy Wait 0
[12991.110864] vc032x: Unknown sensor...
[12991.110897] vc032x: probe of 1-8:1.0 failed with error -22
[12991.113322] usb 1-8: USB disconnect, address 72
[12991.384121] usb 1-8: new high speed USB device using ehci_hcd and address 73
[12991.540424] usb 1-8: configuration #1 chosen from 1 choice
[12991.540795] gspca: probing 046d:0892
[12991.749838] vc032x: check sensor header 44
[12991.751952] vc032x: I2c Bus Busy Wait 0
[12991.754576] vc032x: I2c Bus Busy Wait 0
[12991.757578] vc032x: I2c Bus Busy Wait 0
[12991.760703] vc032x: I2c Bus Busy Wait 0
[12991.765717] vc032x: I2c Bus Busy Wait 0
[12991.767699] vc032x: I2c Bus Busy Wait 0
[12991.767704] vc032x: Unknown sensor...
[12991.767734] vc032x: probe of 1-8:1.0 failed with error -22
[12991.768995] usb 1-8: USB disconnect, address 73
[12992.010254] usb 1-8: new high speed USB device using ehci_hcd and address 74
[12992.171913] usb 1-8: configuration #1 chosen from 1 choice
[12992.173256] gspca: probing 046d:0892
[12992.382637] vc032x: check sensor header 44
[12992.384841] vc032x: I2c Bus Busy Wait 0
[12992.387198] vc032x: I2c Bus Busy Wait 0
[12992.389582] vc032x: I2c Bus Busy Wait 0
[12992.391579] vc032x: I2c Bus Busy Wait 0
[12992.393963] vc032x: I2c Bus Busy Wait 0
[12992.395958] vc032x: I2c Bus Busy Wait 0
[12992.395963] vc032x: Unknown sensor...
[12992.395992] vc032x: probe of 1-8:1.0 failed with error -22
[12992.397267] usb 1-8: USB disconnect, address 74
[12992.668113] usb 1-8: new high speed USB device using ehci_hcd and address 75
[12992.824397] usb 1-8: configuration #1 chosen from 1 choice
[12992.824773] gspca: probing 046d:0892
[12993.032512] vc032x: check sensor header 44
[12993.034586] vc032x: I2c Bus Busy Wait 0
[12993.036715] vc032x: I2c Bus Busy Wait 0
[12993.038709] vc032x: I2c Bus Busy Wait 0
[12993.040839] vc032x: I2c Bus Busy Wait 0
[12993.042827] vc032x: I2c Bus Busy Wait 0
[12993.045077] vc032x: I2c Bus Busy Wait 0
[12993.045083] vc032x: Unknown sensor...
[12993.045111] vc032x: probe of 1-8:1.0 failed with error -22
[12993.045437] usb 1-8: USB disconnect, address 75
[12993.316116] usb 1-8: new high speed USB device using ehci_hcd and address 76
[12993.472437] usb 1-8: configuration #1 chosen from 1 choice
[12993.472925] gspca: probing 046d:0892
[12993.680857] vc032x: check sensor header 44
[12993.682963] vc032x: I2c Bus Busy Wait 0
[12993.684961] vc032x: I2c Bus Busy Wait 0
[12993.686957] vc032x: I2c Bus Busy Wait 0
[12993.689106] vc032x: I2c Bus Busy Wait 0
[12993.691079] vc032x: I2c Bus Busy Wait 0
[12993.693337] vc032x: I2c Bus Busy Wait 0
[12993.693343] vc032x: Unknown sensor...
[12993.693374] vc032x: probe of 1-8:1.0 failed with error -22
[12993.693687] usb 1-8: USB disconnect, address 76
[12993.964062] usb 1-8: new high speed USB device using ehci_hcd and address 77
kaneda@falcon-core:~$ 

```

---

### Post by adam_kimber on 2009-07-08
Confirms a theory. I think your Memory Stick might not be recognised as its "non-standard". We will see. Here are your problems.  

12969.569584] vc032x: Unknown sensor and 
probe of 1-8:1.0 failed with error -22 indicate that. 

Further diagnosis needed. I wonder, does the reader recognise other cards?

---

### Post by Kaneda187 on 2009-07-13
hey sorry haven't got back to this in a while been busy, to answer your question, yes the reader recognizes a range of different cards just not the sony magic gate ones...

---

### Post by mariatamis on 2009-07-13
No need to worry, Magic Gate digital rights managent (DRM) is now standard
on all new Sony Memory Stick cards. It does not affect the operation of the
card on your camera.

---

### Post by Kaneda187 on 2009-07-14
so because of the DRM you cant use it on linux or what?

---

### Post by Kaneda187 on 2009-07-15
Im still a bit confused on this subject could someone please clear it up for me...
thanks

---

### Post by adam_kimber on 2009-07-18
Hmmm this seems to be a unique problem! I cannot find anything on Google etc. 

As for the DRM bit. Looks like MagicGate DRM is hardware, therefore it will need to be supported. However I am sure it would be supported as its fairly common........

---

