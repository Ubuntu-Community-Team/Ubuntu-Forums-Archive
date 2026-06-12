---
title: "The missus PC keeps shutting off"
date: 2016-04-24
forum: Hardware
---

### Post by Sableyes on 2016-04-24
Using Ubuntu, Kubuntu, XUbuntu and Mint. 

The processor runs up to 50-60 degrees then the system turns off. No warning or shut down program, it just turns off in a second. 

The stuff in her PC is as follows :

Asus Sabertooth 990fx r2 
Nvidia Asus geforce gtx 760
Amd piledriver fx-8320 3.5ghz
Arctic freezer a11 processor fan
16gb (2x8gb) corsair vengeance black
950w otx modular power supply
Cooler master k380 tower

It usually happens when she's playing games, Second Life or Anomaly. 

The power supply has been changed for a cooler master 750, still crashed. Thermal paste has been reapplied to processor, twice, still crashed.

---

### Post by T.J. on 2016-04-25
> **Sableyes said:**
> Using Ubuntu, Kubuntu, XUbuntu and Mint. 

The processor runs up to 50-60 degrees then the system turns off. No warning or shut down program, it just turns off in a second. 

The stuff in her PC is as follows :

Asus Sabertooth 990fx r2 
Nvidia Asus geforce gtx 760
Amd piledriver fx-8320 3.5ghz
Arctic freezer a11 processor fan
16gb (2x8gb) corsair vengeance black
950w otx modular power supply
Cooler master k380 tower



I do not know your level of skill, so please humor me. 

 Most AMD processors in that generation should run no hotter than about 40-46C under a full load for over an hour in a room with a temperature of about 23C (75F).  So if you are saying you are hitting the 50's regularly, something is definitely wrong.  If you are overclocking it, you should stop.  Clearly, it is having a problem, and is not stable. Overclocking it can damage it permanently.

The maximum safe die temperature for your processor under normal conditions is 62 C.  If it is running at 50 to 60 degrees C, then something is wrong with your processor installation, and the thermal protection is shutting it down if it spikes suddenly into higher levels. It is true you can exceed 62, but I wouldn't recommend it as it can cause damage.  As a rule, it is always wise to never exceed the recommended maximums, even if the processor can physically withstand it, because the processor's logic can become unstable.  You can have some rather unpleasant side-effects, such as random crashes or corrupted data.

 Most likely, your heat-sink is not seated properly on the processor, regardless of the paste. You may have used the paste incorrectly, which can be as bad as not using enough.  Don't gob it on like most people do or you can get air bubbles in the paste. 

[https://www.youtube.com/watch?v=rjF5jabXRCY](https://www.youtube.com/watch?v=rjF5jabXRCY)

  Also, **do not use your fingers**.  Not only are they carrying dirt and oil, but the chemicals in the paste are toxic, and it may be possible to absorb them through the skin. You do not want them on your skin for extended periods and you certainly do not want to risk ingesting them.  If you come in contact with the paste, you should wash it off** immediately** just to be safe.  I recommend a tool or surgical gloves because some pastes contain some rather unpleasant things which can make you very ill.


The assembly might not be mounted properly. This needs to be checked very diligently. Everything must be tightly secured and not loose. It is also possible that your heat-sink fan or airflow in the case is insufficient.  The air should flow from the front of the case, past the processor to exit the top or the rear.

Under rare cases, there are some games that offload calculations that should be done on the video card to the main CPU causing thermal spikes, which along with a poorly mounted sink will cause it to shut down. I'd check that heat-sink first to make certain it is mounted correctly, and that the fins are free of dust and dirt.

---

### Post by Sableyes on 2016-04-25
Hi T.J.

Thanks for the reply! We have built a number of PC's in the past (this is the 8th I believe) and taken apart and upgraded 2 laptops. I am not a computer wizzard, but I do know my way around :)

The processor came with heat sink. We figured there was an issue with it, so re applied. No change, everyone said 'heat sink' so we did it a third time. The problem remained. We are pretty sure its not heat sink. :)

---

### Post by pfeiffep on 2016-04-25
> **Sableyes said:**
> Hi T.J.

Thanks for the reply! We have built a number of PC's in the past (this is the 8th I believe) and taken apart and upgraded 2 laptops. I am not a computer wizzard, but I do know my way around :)

The processor came with heat sink. We figured there was an issue with it, so re applied. No change, everyone said 'heat sink' so we did it a third time. The problem remained. We are pretty sure its not heat sink. :)My experience with a laptop might help. Using an old Dell Inspiron I noticed when using it as a normal laptop [resting on my lap] after a period of time it would shut itself down rather uncerimoniously. I decided to employ a laptop rest with holes in it to provide a freer air flow - this fixed the problem. 

Apologies if you've already tried these suggestions:
[LIST]
[*]clean the interior completely
[*]insure the fan's working - check if there's a defective temperature controlled fan and possibly the software is running
[*]raise the unit off the floor a bit
[*]temporarily use a small window fan to move air around the pc's placement
[/LIST]

---

### Post by T.J. on 2016-04-25
> **Sableyes said:**
> Hi T.J.

Thanks for the reply!

 
You're very welcome!  I am a software engineer and computer technician, so I usually end up hip deep in this anyway.  It's no trouble.

> 
We have built a number of PC's in the past (this is the 8th I believe) and taken apart and upgraded 2 laptops. I am not a computer wizzard, but I do know my way around :)


I know what you mean. I'm a do-it-yourself person too. =)   The one thing I won't fix is monitors.  Flat-screen lighting systems can contain mercury that can be absorbed through the skin or inhaled, so they should not be disassembled outside of a shop without proper gear.

> 
The processor came with heat sink. We figured there was an issue with it, so re applied. No change, everyone said 'heat sink' so we did it a third time. The problem remained. We are pretty sure its not heat sink. :)

That is an unusual result after re-seating it three times, but your core temperatures are much too high! Check to see if your measurement software is taking an offset into account. I would consider replacing the cooler and bracket when we are finished, regardless. In my experience, I almost never use a stock (cooler sold with processor), because they are usually dreadfully inadequate. 

 AMD processors in particular have a habit of overwhelming a stock cooler, either by acoustics or heat transfer. It has become noted so often, that AMD has redesigned their stock coolers, and now uses a Wraith heat-sink.  [https://www.youtube.com/watch?v=soc5x_4IACQ](https://www.youtube.com/watch?v=soc5x_4IACQ)  I hope it isn't the cooler, after all of that effort, but it can't be entirely ruled out unless you try replacing it.  

The next thing I would try under the circumstances is verifying that your PSU (power supply) is not faulty or inadequate. They can shutdown intermittently if they are overheating or if the processor, drives, and video card are too much of a draw.  I'm guessing from your specs, it may be a heating issue rather than a brown-out.  As you have a modular one, I would check the cables also.  They have been known to come loose. 

The next time it shuts down, feel the backfan - it is feels excessively hot, it is likely you are overheating the PSU, and need to replace it.  You can also get strange effects from memory banks that have been jarred, and need to be re-seated in the socket.

I'd also verify your power management settings in your firmware and OS.  Heaven knows that not all ACPI implementations are decent.  Some of them should require a "Mr. Yuk" sticker.

---

