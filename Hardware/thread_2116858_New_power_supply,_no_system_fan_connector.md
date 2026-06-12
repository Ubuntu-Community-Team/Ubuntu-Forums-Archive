---
title: "New power supply, no system fan connector"
date: 2013-02-16
forum: Hardware
---

### Post by Acharn on 2013-02-16
I was surprised not to find this question addressed before. I want to upgrade my graphics card, so I was warned that I would need a better power supply. I have an old Acer Aspire M1610, which has a 250W PSU, I intended to buy a cheap 450@, but the salesman persuaded me I needed better than that, so I got a Raidmax RX-630SS. When I started to remove the old power supply I gound a 3-pin connector to what is labeled "system fan" on the motherboard. There is no similar connector among the cables for the new PSU. Should I take i back to the store and get a different PSU?

In addition, the old connector is very hard to remove. Many years ago when I was dealing with hardwar maintenance more often the connector came off easily -- there's no lever to press to release. I'm working with an Acer F672CR motherboard here, and the Service Guide doesn't show anything. Should I just keep pulling harder?

---

### Post by Yellow Pasque on 2013-02-16
The PSU has its own internal fan controller.

---

### Post by CharlesA on 2013-02-16
RAIDMAX PSUs are the bottom of the barrel. You'd be better off getting something else.

The system fan connector on the motherboard should be going to a case fan.

The power supply should have been plugged into two places on the motherboard - a P4 (or P8, maybe) connector with 4 or 8 pins and an ATX connector with 20 or 24 pins.

Specs are here:
[http://support.acer.com/acerpanam/desktop/0000/Acer/AspireM1610/AspireM1610sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireM1610/AspireM1610sp2.shtml)

---

### Post by oldfred on 2013-02-16
I thought it was one of the cables that plugged into another connector and branched off with the smaller fan connector and another for hard drive or something else.

But last time I had a power supply cable with the 3 pin connector and I need 4 as that gives variable speed or something worthwhile. Fan control is different than all the other connectors.

---

### Post by CharlesA on 2013-02-16
> **oldfred said:**
> I thought it was one of the cables that plugged into another connector and branched off with the smaller fan connector and another for hard drive or something else.

Probably one of these:
[http://www.amazon.com/Fan-4-Wire-Molex-Connector/dp/B000BSN5TE](http://www.amazon.com/Fan-4-Wire-Molex-Connector/dp/B000BSN5TE)


> But last time I had a power supply cable with the 3 pin connector and I need 4 as that gives variable speed or something worthwhile. Fan control is different than all the other connectors.

The only fan i've seen use a 4 pin connector is the CPU fan. All other ones I've seen use 3 pins - one for power, one for ground and one for the speed - via PWM usually.

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by Acharn on 2013-02-17
> **Temüjin said:**
> The PSU has its own internal fan controller.

Yes, That's not the problem. According to the Service Manual for the motherboard there's a fan mounted at the back of the case that they call the "System Fan". That fan connects to a point on the motherboard between the CPU and the rear of the case. Just behind the HDD, on the motherboard, is a point with three pins that the Service Manual says,

```
8. Connect the System Fan power connector to the MB connector.
```
 I used to do maintenance on a bunch of PCs for a school, and some of them had this feature, most did not. Usually when we bought new power supplies they did not have this "System Fan power connector" and I used to just ignore them, never had a heating problem but we're talking ten years ago and more.

---

### Post by Yellow Pasque on 2013-02-17
Oh... well you would need to plug a fan there (probably not the PSU). So just to confirm, your CPU does have its own fan and own fan connector, correct?

Did your old PSU have an external 3-pin fan connector? If so, how many wires were going to it? My last PSU had that connector, but it was only a 2-wire affair for the purpose of monitoring the PSU fan's RPM and making sure it was still kicking.

---

### Post by Acharn on 2013-02-17
> **ahallubuntu said:**
> On older motherboards without system fan connectors (not "CPU fan"), the case fan could be hard wired to the power supply with an adapter.  But if you did so, it would always run at 100% speed and could not be monitored or controlled by the motherboard.

If your old PSU truly has a hard wire connector (not an adapter) to connect to a case fan, you could buy an adapter to do the same thing using one of the 4-pin old-style molex connectors and plug the adapter in there.  But if for some reason the motherboard really does have a sysfan connector and it was just overlooked before, try to use that instead.

OK, I think this may be the solution. I need to find out what voltage that System Fan power connector is carrying.

---

### Post by Yellow Pasque on 2013-02-17
I think you're making it too difficult. As long as your CPU has its own fan/connector, you don't need to plug anything into that fan connector.

---

### Post by Acharn on 2013-02-17
> **CharlesA said:**
> RAIDMAX PSUs are the bottom of the barrel. You'd be better off getting something else.

The system fan connector on the motherboard should be going to a case fan.

The power supply should have been plugged into two places on the motherboard - a P4 (or P8, maybe) connector with 4 or 8 pins and an ATX connector with 20 or 24 pins.

Specs are here:
[http://support.acer.com/acerpanam/desktop/0000/Acer/AspireM1610/AspireM1610sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireM1610/AspireM1610sp2.shtml)

Yes, that's the right spec sheet. The ATX connector is 24 pins, that one's no problem. My problem is with the  case fan connector. How do I get the damn thing off? I never had a problem before, they always just slid off. Of course this one has been in place for five and a half years, so mayb it's just stuck and I need to pull harder, but I'm leary of breaking something.

I'm darned glad Acer put their Service Manual for this motherboard online and it has pictures, but sometimes the pictures are not as clear as I would wish.

---

### Post by Yellow Pasque on 2013-02-17
> I'm darned glad Acer put their Service Manual for this motherboard online and it has pictures
Link?

---

### Post by Acharn on 2013-02-17
> **Temüjin said:**
> Oh... well you would need to plug a fan there (probably not the PSU). So just to confirm, your CPU does have its own fan and own fan connector, correct?

Did your old PSU have an external 3-pin fan connector? If so, how many wires were going to it? My last PSU had that connector, but it was only a 2-wire affair for the purpose of monitoring the PSU fan's RPM and making sure it was still kicking.

Yes, the CPU has its own fan which connects elsewhere. The old PSU had three wires going to the connector. These were separate from but parallel to the wires going to the ATX connector. In the Service Manual for the F672CR motherboard, on page 10 of the .pdf or Page 3 (as shown at the bottom of the page) in the right-hand column are shown: "1 3-pin System Fan connector" and just below that "1 24-pin ATX interface PS3/PS2 SPS connector." It's that "System Fan connector" that's bothering me. I can't tell what brand the old PSU is, and the Service Manual just calls it "industry standard 250 watt PSU."

---

### Post by Acharn on 2013-03-05
OK, it took a while because I was suffering too much anxiety. In the end it was nearly as easy as I remembered. The newer computers are less easy to work in, but I finally managed.

First, and I think it's important, the System Fan Power Connection that I was asking about is actually a set of wires, red-yellow-black, that are from the case fan. I was confused because when they assemblet this thing thay put the wires together with all the other wires from the power supply and bound them together with plastic cable ties. When I finally worked up enough nerve to cut the cable ties I was able to separate those wires from the power supply wires. The connector is all the way at the front of the motherboard, right behind the hard drive. I am not an engineer, so I suppose there is some reason that would be blindingly obvious to an engineer why it makes sense to have the pwer connection for the case fan so far away from the fan, which is mounted in the rear of the case. The connector has to be tilted forward to be released, and that memory had become dim over the years but finally came back to me.

This is an Acer Aspire M-1610 desktop model I'm working with, and the CPU cooling unit has a funnel-shaped thingy that has to be moved. That really scared me, but when I went ahead and started removing screws it wasn't as bad as I feared. My biggest worry was that I would drop one or more of the small screws, but happily that didn't happen. There was a lot of dust matted on the top of the heat sink, and I think the thing will run cooler now with that removed (I've been using this box for over five years now -- it never occurred to me to check this out).

So thank you to everybody who tried to help me with this. I don't know what wires are carrying the info about CPU or case temperature, but I don't really care about that. Marking this thread [solved].

---

### Post by CharlesA on 2013-03-05
Magnetic screwdriver = godsend. ;)

Glad you were able to figure things out. I don't even know why they would have ziptied a fan connector that goes no where near the power supply in with the PSU cables.

---

### Post by Acharn on 2013-03-06
Just to keep things tidy, I suppose. The case fan is on the back of the case, just below the PSU, The power line has to come along the top of the case all the way to the front then makes a 90 degree turn and goes all the way down to the bottom. There's a four-pin connector from the power supply to a connector on the motherboard quite near the fan, so it seemed reasonable to bundle them together. It keeps space open for air circulation and keeps wires from falling onto components which might get hot. As I said in another post, I'm not an engineer but I presume an engineer would see potential problems I don't. I slept on it for several nights before the situation came to me during one of my dozing periods.

---

