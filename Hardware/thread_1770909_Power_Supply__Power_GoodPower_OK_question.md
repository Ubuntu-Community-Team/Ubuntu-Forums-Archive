---
title: "Power Supply:  Power_Good/Power OK question"
date: 2011-05-29
forum: Hardware
---

### Post by held7over on 2011-05-29
This probably isn't exactly the right forum to ask this, but the forum I would use for this evidently is suffering from the havoc of the Joplin Tornado...the worst tornado since 1947.

A friend who I am converting to Ubuntu has a Tower which is not sending a signal to my Flat Screen. I have a Coolmax PS-229 Power Supply tester I have never used. So, I disconnected all of the power supply wiring inside the tower as it directed, plugged in the 20 pin board connector into the Tester and the 4 pin wire, again as directed. Turned on the power. And had the tester take a sample. It's alarm is signaling a problem and is reporting the Power Good signal, also known as the Power OK signal from the Power Supply is taking far longer than 900 ms (which the table says is the max) to report the Power Supply's stability. I have no idea what a Power Good signal is or why it would have to report within the given time frame...)

All the voltage readings though, seem to be correct or within tolerances. Of course, this is without being under a load.....since I disconnected all the components from power. 

What is the implication of this fault condition? Can I take that to mean the power supply is unstable and should be replaced?

Thanks for any help you can offer on this! :p

---

### Post by tgalati4 on 2011-05-29
If you have a failing capacitor in the power supply, it may provide sufficient voltage on each channel (1.5, 3.3, 5, 12 VDC, etc), but it may fail (drop voltage) when under load.  The reason you want it to come up quickly (900 ms which is less than 1 sec) is it shows that your capacitors are holding charge.  If it takes longer, then you might have a leaky capacitor that takes longer to charge up.  It's subjective, but a quick way to spot a problem.  Does it apply to all computer power supplies?  Who knows.  There are several designs out there and all sorts of quality issues--poor capacitors, poor MOSFETs, crappy soldering, etc.

If the computer runs at full bore--watching a high definition video, for instance, then it should be OK.  Running HD video taxes the CPU, the GPU, and the hard disk all at once.  If the machine can handle playing 1 hour of HD video, then I would say it's OK, regardless of what the tester says.  Use an UPS regardless--it will provide more protection than a power strip.

---

### Post by held7over on 2011-05-30
Thanks for the explanation tgalati4. I understand now what the significance is.

Before moving on to the next component, I need to make a determination if the power supply is actually working correctly or not. [COLOR="Black"]Right now, my friend's tower is not sending a video signal to my Flat Screen.[/COLOR] The first thing I did in troubleshooting was to install a different video card (I had a spare), and that apparently isn't the problem, as my Flat Screen continues to say no signal. So, I figured the power supply should be checked next (since I had this never used Power Supply Tester).

Any suggestions as to how to proceed? Maybe I should plug all the peripheral components to the Motherboard back into power, and then try testing the leads one at a time with the Power Supply Tester and see what kind of reading I get under load?

---

### Post by held7over on 2011-05-30
The answer is:  There is no need to check the power supply further.

I found the answer here:  [http://en.wikipedia.org/wiki/Power_Good_Signal](http://en.wikipedia.org/wiki/Power_Good_Signal)

In addition to the voltages and currents that a computer needs to operate, power supplies also provide a signal called the Power-Good signal, sometimes written as Power_OK or Power_Good or you can distinguish it by its gray color. Its purpose is to tell the computer all is well with the power supply and that the computer can continue to operate normally. If the Power-Good signal is not present at startup, the CPU is held in reset state. If a Power-Good signal goes down during operation the CPU will shutdown. The Power-Good signal prevents the computer from attempting to operate on improper voltages and damaging itself.

The ATX specification defines the Power-Good signal as a +5 volt (V) signal generated in the power supply when it has passed its internal self-tests and the outputs have stabilized. This normally takes between 0.1 and 0.5 seconds after the power supply is switched on. The signal is then sent to the motherboard, where it is received by the processor timer chip that controls the reset line to the processor.

In the absence of the Power-Good signal, the timer chip continuously resets the processor, which prevents the computer from running under bad or unstable power conditions. When the timer chip receives the Power-Good signal, it stops resetting the processor, and then the processor executes whatever code is at address FFFF:0000 (usually the ROM BIOS).

If the power supply cannot maintain proper outputs, such as when a brownout occurs, the Power-Good signal is withdrawn, and the processor is automatically reset. When proper output is restored, the Power-Good signal is regenerated, and the computer again begins operation. By withdrawing the Power-Good signal, the computer never receives the bad power because it is stopped quickly (reset) rather than allowed to operate on unstable or improper power levels, which can cause parity errors and other problems.

Cheaper and/or lower quality power supplies do not follow the ATX specification of a separate monitoring circuit; they instead wire the power good output to one of the 5V lines. This means the processor will never reset given bad power unless the 5V line drops low enough to turn off the trigger, which could be too low for proper operation.

---

