---
title: "Serial printing problems"
date: 2014-08-07
forum: Hardware
---

### Post by arild2 on 2014-08-07
[COLOR=#333333][FONT=UbuntuRegular]I'w tried every tips i have found. I cant get my Star termic printer to work. After my Win server died, i installed a Ubuntu 13.? server with LAMP I have a receipt printer attached to it an here is my Win lines witch did work.[/FONT][/COLOR]
  `mode COM2: BAUD=19200 PARITY=N data=8 stop=1 xon=off`;
  $sp = fopen("COM2", "w+");
  fwrite($sp,"Test");
  fclose($sp);
[COLOR=#333333][FONT=UbuntuRegular]I have configured the baud to 19200 and it do print "greek" and a lot of "?"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Tips anyone???[/FONT][/COLOR]

---

