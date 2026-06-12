---
title: "Laptop Battery brush off?"
date: 2010-03-14
forum: Hardware
---

### Post by BrockStrongo on 2010-03-14
Hello,
So I ordered a new "high capacity" laptop battery off ebay. After a couple full cycles it only shows 77 % of capacity. I fired off an email to the store it came from, here it is.
 
[SIZE=2]**Dear masterdealalert,**[/SIZE]
[SIZE=2]Hi,[/SIZE]
[SIZE=2]I recently purchased the above item. After two full charge and discharge cycles the battery is only showing 77.1% of it's expected capacity.[/SIZE]
[SIZE=2]49 wh instead of 64 as adverstised.[/SIZE]
[SIZE=2]Please advise as to what my next action should be.[/SIZE]
[SIZE=2]Thanks [/SIZE]
 
My hopes were he would respond saying "oh it's defective, send it back andI will send another"
no such luck :( 
Here is what I got in return
 
HI:
 
This is normal
 
laptop software will only see approx 4000-4400mah since that is the highest acer makes for this model 
 
so it shows 4400divided by 5800mah= approx 75%
 
Than you
 
So, am I getting the brush off or is this guy telling the truth. 
P.S. After a deep discharge and recharge it is now showing 78% 50.1 wh
Thanks for the help

---

### Post by BrockStrongo on 2010-03-14
anyone?......
Has this happened to anyone?
All opinions welcome

---

### Post by leorolla on 2010-03-15
One test you can do is to see how long it will take it to drop from 77%.

If what they say is true, you will go all the way down from 5800 to 4400 (and that will take quite a while) without seeing any change at all.

---

### Post by tgalati4 on 2010-03-15
If you are running the gnome applet battery monitor, you will get discharge and charge curves.  

Math warning:

If you take the integral of the discharge curve (the area under the curve) you should get the actual, observed capacity in watt-hours.  Don't confuse ampacity rating with wattage rating.  Power==wattage==average volts sustained*amps delivered.  Capacity==watts*time delivered==watt*hours typically.

Over time, the gnome battery monitor gets more accurate in its battery-life prediction as it gains more cycles.

Where is the battery made?

Battery life/capacity claims are often misstated.

---

### Post by BrockStrongo on 2010-03-15
I'm not sure where the battery was made. The simplo factory appears to be in China
here is gnome power manager details

Product: Laptop battery
Status: Charging
Percentage charge: 85.3%
Vendor: SIMPLO
Technology: Lithium Ion
Serial number: 305
Model: AS07B71
Charge time: 1 minute
Capacity: 78.6% (Fair)
Current charge: 43.2 Wh
Last full charge: 50.6 Wh
Design charge: 64.4 Wh
Charge rate: 704.6 W
Thanks for the replies so far this is helping a lot

---

### Post by leorolla on 2010-03-16
Did you try the test I suggested?

Run it on battery and see how long it takes to drop from 78.6% to, say, 75%.

---

### Post by tgalati4 on 2010-03-16
Yes, it certainly appears that you are only getting 50.6 watthours of capacity.  The rating of 64.4 watthours is probably some engineering estimate based on the sum of the individual cell capacities.

There are many battery cell manufacterers.  Some are better than others.  All it takes is one weak cell (out of 6 or 9) to reduce the capacity of the entire pack.

A search on simplo:  (And this builds confidence)

"This Site Under Renovation, Sorry For The Inconveince"

Simplo is a manufacture of high quality, cost competitive battery packs for Laptop Computers, PDA's, Hand Held Test Equipment, Cell phones, Cordless Phones and Custom Packs as per customer specifications. In addition we design, build & test Li-Ion Protection PCB's, SMBus Fuel Gauges and special application PCB's

Simplo is also a suppiler of Ni-Cad, Ni-MH & Li-Ion cells in Cylindrical and Prismatic form factors. And coming soon Lithium Polymer cells.

  Phone: (510) 713-7914             Business Hours: Monday - Friday  
  Fax:   (510) 794-9796                             8:00am  - 5:00pm PST 
  or Email us at:

--------------

From the CEO of the Taiwanese company:

Sung said that the lithium-ion battery market is mainly dominated by makers in five nations: American companies like A123, Johnson`s control, EnerDel, Boston Power etc.; mainland Chinese makers as BYD, Amperex Technology, Tianjin Lishen Battery, BAK, Coslight, ATL etc.; Japanese firms as Toshiba, Panasonic, Sanyo Sony, NEC etc.; South Koreans as LGC, SBL etc.; and Taiwanese as Lanyo, Amita Technologies, Molicel, Phoenix Silicon International etc.

Not for Everyone
"The current lithium-ion battery market is haphazard and chaotic with many small companies joining the game without meeting unified specifications, sizes, and performance standards," Sung said. "Simplo being a battery packer rather than cell maker, I think only 10% of the existing cell makers will survive. No amateurs can make good batteries, especially overnight, as the business calls for major investments and cutting-edge technologies." 

----------------------

So unless Simplo checks the quality of the individual cells (and who knows what they contain--catfood perhaps?) you may not get the rated capacity.

---

### Post by BrockStrongo on 2010-03-16
I ran the aforementioned test and the time it took to drop from 78.6% to 75% while resting idle was about 4 minutes. This seems to be the same rate as any other drop of 3.* %
Thanks for your help with this

---

### Post by leorolla on 2010-03-16
> **BrockStrongo said:**
> Hello,
HI:
 
This is normal
 
laptop software will only see approx 4000-4400mah since that is the highest acer makes for this model 
 
so it shows 4400divided by 5800mah= approx 75%
 
Than you
 

So, this does not make any sense at all.

If "laptop software only see 4000mah" but the battery is charged at 5800mah, how does software onlye see 3900mah after 4 minutes?!

---

### Post by tgalati4 on 2010-03-16
He's blowing smoke.

The gnome power manager is simply reading values off of the battery's nonvolatile RAM.  The battery's charging circuit maintains those values for warranty purposes.  Many companies (like Apple) will warranty their batteries to maintain 80% of capacity up to 300 cycles.  So they rely on these values to determine warranty claims.  I know, since I've had several Apple batteries replaced.

Looks like your battery simplo doesn't measure up.

---

