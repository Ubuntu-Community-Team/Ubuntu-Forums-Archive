---
title: "Toshiba Qosmio x775 subwoofer not working"
date: 2014-07-30
forum: Hardware
---

### Post by ramirezv1968 on 2014-07-30
I installed Ubuntu 14.10 in a Toshiba Quosmio X775  and in all versions the internal sub-woofer doesn't work.

I tried adding this line to default.pa

**load-module module-combine channels=3 channel_map=front-left,front-right,lfe**

also tried:

**load-module module-combine channels=6 channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe**


and in daemon.conf tried:

**default-sample-channels = 3**
**default-channel-map = front-left,front-right,lfe**



and also tried with:

**default-sample-channels = 6**
**default-channel-map = ****front-left,front-right,rear-left,rear-right,front-center,lfe**

Now if I go to the "Sound Settings" I can see a new option that says "Simultaneous output to Built-in Audio Digital Stereo (HDMI)" and I can see a slider to change the volume of the sub-woofer.  If I select the button "Test Sound" I can see either 6 speaker or 3 speakers depending on what I have in the parameters of the two files mentioned above.  However, if I press the "Test" button for the Subwoofer the test sound is played by the main speakers, not the sub-woofer.  I even connected an HDMI TV and the sound of the sub-woofer then goes to the TV but never to the actual sub-woofer in the laptop.

---

### Post by ramirezv1968 on 2014-07-31
Sorry, its Ubuntu 14.04LTS not 14.10 :oops:

Please, any help will be appreciated.

Thanks.

---

