---
title: "Is This Being Cheeky (Microsoft Headset)"
date: 2009-01-06
forum: Hardware
---

### Post by 5BallJuggler on 2009-01-06
I have a Microsoft LifeChat LX-3000 headset and i'm trying to make it work with Ubuntu, specifically with VirtualBox 2.1 running XP inside Ubuntu.

I have managed to get it to operate, but the audio through the headphones is very "Choppy", and I can't confirm the microphone clarity because i'm unable to hear anything on the other end.
the reason i'm running VirtualBox 2.1 is to enable the use of my Spykee robot, but ideally i'd like to be able to use the headset while using skype.

Does anyone have any ideas how the issue can be fixed

also, I think it may be causing a hardware conflict somewhere, some of my hard drives have become unmountable until i go into windows and shut them down manually.

I understand that this is more than one problem, but i'm hoping there is a common fix.

Thanks

Phil

---

### Post by 5BallJuggler on 2009-01-07
update, 
today i tried to use the headset in Ubuntu (not VirtualBox), it does not appear to work as a headphone set at all.
the unit has 4 buttons that control volume, mute and allow you to open a call connection, the volume buttons open a "mini applet" that shows a speaker, the other to appear not to work at all.

how do i configure a USB device?

---

### Post by 5BallJuggler on 2009-01-07
I'm also getting this error when i change the settings in the sound preferences.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Internal data flow error.

And sometimes I get this one too.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

tried in both ALSA and OSS modes

This is the output of the dmseg command

```
[83996.148468] 2:2:1: usb_set_interface failed
[83997.216891] 2:1:1: usb_set_interface failed
[83997.218743] 2:1:1: usb_set_interface failed
[83997.219679] 2:1:1: usb_set_interface failed
[83997.220604] 2:1:1: usb_set_interface failed
[83997.221528] 2:1:1: usb_set_interface failed
[83997.222346] 2:1:1: usb_set_interface failed
[83997.223167] 2:1:1: usb_set_interface failed
[83997.224019] 2:1:1: usb_set_interface failed
[83997.234028] 2:1:1: usb_set_interface failed
[83997.234347] 2:1:1: usb_set_interface failed
[83997.234558] 2:1:1: usb_set_interface failed
[83997.235390] 2:1:1: usb_set_interface failed
[83997.236408] 2:1:1: usb_set_interface failed
[83997.237356] 2:1:1: usb_set_interface failed
[83997.238188] 2:1:1: usb_set_interface failed
[83997.239027] 2:1:1: usb_set_interface failed
[83997.239867] 2:1:1: usb_set_interface failed
[83997.241103] 2:2:1: usb_set_interface failed
[83997.241942] 2:2:1: usb_set_interface failed
[83997.242786] 2:2:1: usb_set_interface failed
[83997.242880] 2:2:1: usb_set_interface failed
[83997.242952] 2:2:1: usb_set_interface failed
[83997.243011] 2:2:1: usb_set_interface failed
[83997.243074] 2:2:1: usb_set_interface failed
[83997.243139] 2:2:1: usb_set_interface failed
[83997.243210] 2:2:1: usb_set_interface failed
[83997.243290] 2:2:1: usb_set_interface failed
[83997.243357] 2:2:1: usb_set_interface failed
[83997.243418] 2:2:1: usb_set_interface failed
[83997.243488] 2:2:1: usb_set_interface failed
[83997.243552] 2:2:1: usb_set_interface failed
[83997.243625] 2:2:1: usb_set_interface failed
[83997.243700] 2:2:1: usb_set_interface failed
[83997.243776] 2:2:1: usb_set_interface failed
[83997.243926] 2:1:1: usb_set_interface failed
[83997.244052] 2:1:1: usb_set_interface failed
[83997.244137] 2:1:1: usb_set_interface failed
[83997.244227] 2:1:1: usb_set_interface failed
[83997.244300] 2:1:1: usb_set_interface failed
[83997.244361] 2:1:1: usb_set_interface failed
[83997.244424] 2:1:1: usb_set_interface failed
[83997.244491] 2:1:1: usb_set_interface failed
[83997.244564] 2:1:1: usb_set_interface failed
[83997.244653] 2:1:1: usb_set_interface failed
[83997.244722] 2:1:1: usb_set_interface failed
[83997.244785] 2:1:1: usb_set_interface failed
[83997.244856] 2:1:1: usb_set_interface failed
[83997.244922] 2:1:1: usb_set_interface failed
[83997.244992] 2:1:1: usb_set_interface failed
[83997.245069] 2:1:1: usb_set_interface failed
[83997.245147] 2:1:1: usb_set_interface failed
[83997.245237] 2:2:1: usb_set_interface failed
[83997.245316] 2:2:1: usb_set_interface failed
[83997.245401] 2:2:1: usb_set_interface failed
[83997.245492] 2:2:1: usb_set_interface failed
[83997.275051] 2:2:1: usb_set_interface failed
[83997.275122] 2:2:1: usb_set_interface failed
[83997.275188] 2:2:1: usb_set_interface failed
[83997.275258] 2:2:1: usb_set_interface failed
[83997.275330] 2:2:1: usb_set_interface failed
[83997.275412] 2:2:1: usb_set_interface failed
[83997.275479] 2:2:1: usb_set_interface failed
[83997.275539] 2:2:1: usb_set_interface failed
[83997.275614] 2:2:1: usb_set_interface failed
[83997.275678] 2:2:1: usb_set_interface failed
[83997.275747] 2:2:1: usb_set_interface failed
[83997.275821] 2:2:1: usb_set_interface failed
[83997.275899] 2:2:1: usb_set_interface failed
[83997.276127] 2:1:1: usb_set_interface failed
[83997.276207] 2:1:1: usb_set_interface failed
[83997.276290] 2:1:1: usb_set_interface failed
[83997.276380] 2:1:1: usb_set_interface failed
[83997.276450] 2:1:1: usb_set_interface failed
[83997.276509] 2:1:1: usb_set_interface failed
[83997.276571] 2:1:1: usb_set_interface failed
[83997.276639] 2:1:1: usb_set_interface failed
[83997.276710] 2:1:1: usb_set_interface failed
[83997.276791] 2:1:1: usb_set_interface failed
[83997.276858] 2:1:1: usb_set_interface failed
[83997.276919] 2:1:1: usb_set_interface failed
[83997.276989] 2:1:1: usb_set_interface failed
[83997.277053] 2:1:1: usb_set_interface failed
[83997.277121] 2:1:1: usb_set_interface failed
[83997.277197] 2:1:1: usb_set_interface failed
[83997.277273] 2:1:1: usb_set_interface failed
[83997.277362] 2:2:1: usb_set_interface failed
[83997.277443] 2:2:1: usb_set_interface failed
[83997.277529] 2:2:1: usb_set_interface failed
[83997.277624] 2:2:1: usb_set_interface failed
[83997.277697] 2:2:1: usb_set_interface failed
[83997.277758] 2:2:1: usb_set_interface failed
[83997.277822] 2:2:1: usb_set_interface failed
[83997.277889] 2:2:1: usb_set_interface failed
[83997.277962] 2:2:1: usb_set_interface failed
[83997.278045] 2:2:1: usb_set_interface failed
[83997.293953] 2:2:1: usb_set_interface failed
[83997.294064] 2:2:1: usb_set_interface failed
[83997.294141] 2:2:1: usb_set_interface failed
[83997.294210] 2:2:1: usb_set_interface failed
[83997.294280] 2:2:1: usb_set_interface failed
[83997.294357] 2:2:1: usb_set_interface failed
[83997.294436] 2:2:1: usb_set_interface failed
[83997.294611] 2:1:1: usb_set_interface failed
[83997.294693] 2:1:1: usb_set_interface failed
[83997.294778] 2:1:1: usb_set_interface failed
[83997.294869] 2:1:1: usb_set_interface failed
[83997.294941] 2:1:1: usb_set_interface failed
[83997.295001] 2:1:1: usb_set_interface failed
[83997.295064] 2:1:1: usb_set_interface failed
[83997.295130] 2:1:1: usb_set_interface failed
[83997.295202] 2:1:1: usb_set_interface failed
[83997.295284] 2:1:1: usb_set_interface failed
[83997.295352] 2:1:1: usb_set_interface failed
[83997.295414] 2:1:1: usb_set_interface failed
[83997.295485] 2:1:1: usb_set_interface failed
[83997.295550] 2:1:1: usb_set_interface failed
[83997.295623] 2:1:1: usb_set_interface failed
[83997.295700] 2:1:1: usb_set_interface failed
[83997.295777] 2:1:1: usb_set_interface failed
[83997.295865] 2:2:1: usb_set_interface failed
[83997.295946] 2:2:1: usb_set_interface failed
[83997.296059] 2:2:1: usb_set_interface failed
[83997.296149] 2:2:1: usb_set_interface failed
[83997.296222] 2:2:1: usb_set_interface failed
[83997.296283] 2:2:1: usb_set_interface failed
[83997.296346] 2:2:1: usb_set_interface failed
[83997.296413] 2:2:1: usb_set_interface failed
[83997.296486] 2:2:1: usb_set_interface failed
[83997.296568] 2:2:1: usb_set_interface failed
[83997.296641] 2:2:1: usb_set_interface failed
[83997.296703] 2:2:1: usb_set_interface failed
[83997.296775] 2:2:1: usb_set_interface failed
[83997.296841] 2:2:1: usb_set_interface failed
[83997.296911] 2:2:1: usb_set_interface failed
[83997.296988] 2:2:1: usb_set_interface failed
[83997.297065] 2:2:1: usb_set_interface failed
[83997.297177] 2:1:1: usb_set_interface failed
[83997.297257] 2:1:1: usb_set_interface failed
[83997.297342] 2:1:1: usb_set_interface failed
[83997.297432] 2:1:1: usb_set_interface failed
[83997.297504] 2:1:1: usb_set_interface failed
[83997.297564] 2:1:1: usb_set_interface failed
[83997.319087] 2:1:1: usb_set_interface failed
[83997.319164] 2:1:1: usb_set_interface failed
[83997.319239] 2:1:1: usb_set_interface failed
[83997.319321] 2:1:1: usb_set_interface failed
[83997.319389] 2:1:1: usb_set_interface failed
[83997.319450] 2:1:1: usb_set_interface failed
[83997.319520] 2:1:1: usb_set_interface failed
[83997.319588] 2:1:1: usb_set_interface failed
[83997.319656] 2:1:1: usb_set_interface failed
[83997.319732] 2:1:1: usb_set_interface failed
[83997.319809] 2:1:1: usb_set_interface failed
[83997.319921] 2:2:1: usb_set_interface failed
[83997.321694] 2:2:1: usb_set_interface failed
[83997.321785] 2:2:1: usb_set_interface failed
[83997.321876] 2:2:1: usb_set_interface failed
[83997.321948] 2:2:1: usb_set_interface failed
[83997.322009] 2:2:1: usb_set_interface failed
[83997.322072] 2:2:1: usb_set_interface failed
[83997.322138] 2:2:1: usb_set_interface failed
[83997.322210] 2:2:1: usb_set_interface failed
[83997.322291] 2:2:1: usb_set_interface failed
[83997.322360] 2:2:1: usb_set_interface failed
[83997.322422] 2:2:1: usb_set_interface failed
[83997.322493] 2:2:1: usb_set_interface failed
[83997.322559] 2:2:1: usb_set_interface failed
[83997.322632] 2:2:1: usb_set_interface failed
[83997.322708] 2:2:1: usb_set_interface failed
[83997.322785] 2:2:1: usb_set_interface failed
[83997.405036] 2:1:1: usb_set_interface failed
[83997.405124] 2:1:1: usb_set_interface failed
[83997.405209] 2:1:1: usb_set_interface failed
[83997.405298] 2:1:1: usb_set_interface failed
[83997.405370] 2:1:1: usb_set_interface failed
[83997.405429] 2:1:1: usb_set_interface failed
[83997.405491] 2:1:1: usb_set_interface failed
[83997.405557] 2:1:1: usb_set_interface failed
[83997.405636] 2:1:1: usb_set_interface failed
[83997.405716] 2:1:1: usb_set_interface failed
[83997.405784] 2:1:1: usb_set_interface failed
[83997.405845] 2:1:1: usb_set_interface failed
[83997.405915] 2:1:1: usb_set_interface failed
[83997.405979] 2:1:1: usb_set_interface failed
[83997.406047] 2:1:1: usb_set_interface failed
[83997.406123] 2:1:1: usb_set_interface failed
[83997.406199] 2:1:1: usb_set_interface failed
[83997.406290] 2:2:1: usb_set_interface failed
[83997.406370] 2:2:1: usb_set_interface failed
[83997.406455] 2:2:1: usb_set_interface failed
[83997.406545] 2:2:1: usb_set_interface failed
[83997.406622] 2:2:1: usb_set_interface failed
[83997.406683] 2:2:1: usb_set_interface failed
[83997.406746] 2:2:1: usb_set_interface failed
[83997.406815] 2:2:1: usb_set_interface failed
[83997.406890] 2:2:1: usb_set_interface failed
[83997.406972] 2:2:1: usb_set_interface failed
[83997.407041] 2:2:1: usb_set_interface failed
[83997.407104] 2:2:1: usb_set_interface failed
[83997.407175] 2:2:1: usb_set_interface failed
[83997.407242] 2:2:1: usb_set_interface failed
[83997.407312] 2:2:1: usb_set_interface failed
[83997.407389] 2:2:1: usb_set_interface failed
[83997.407466] 2:2:1: usb_set_interface failed
[83997.407615] 2:1:1: usb_set_interface failed
[83997.407695] 2:1:1: usb_set_interface failed
[83997.407780] 2:1:1: usb_set_interface failed
[83997.407870] 2:1:1: usb_set_interface failed
[83997.408132] 2:1:1: usb_set_interface failed
[83997.408199] 2:1:1: usb_set_interface failed
[83997.408263] 2:1:1: usb_set_interface failed
[83997.408332] 2:1:1: usb_set_interface failed
[83997.408408] 2:1:1: usb_set_interface failed
[83997.408490] 2:1:1: usb_set_interface failed
[83997.408560] 2:1:1: usb_set_interface failed
[83997.408627] 2:1:1: usb_set_interface failed
[83997.408699] 2:1:1: usb_set_interface failed
[83997.408766] 2:1:1: usb_set_interface failed
[83997.408836] 2:1:1: usb_set_interface failed
[83997.408914] 2:1:1: usb_set_interface failed
[83997.408992] 2:1:1: usb_set_interface failed
[83997.409082] 2:2:1: usb_set_interface failed
[83997.409163] 2:2:1: usb_set_interface failed
[83997.409248] 2:2:1: usb_set_interface failed
[83997.409338] 2:2:1: usb_set_interface failed
[83997.409412] 2:2:1: usb_set_interface failed
[83997.409473] 2:2:1: usb_set_interface failed
[83997.409537] 2:2:1: usb_set_interface failed
[83997.409610] 2:2:1: usb_set_interface failed
[83997.409686] 2:2:1: usb_set_interface failed
[83997.409804] 2:2:1: usb_set_interface failed
[83997.409874] 2:2:1: usb_set_interface failed
[83997.409937] 2:2:1: usb_set_interface failed
[83997.410010] 2:2:1: usb_set_interface failed
[83997.410077] 2:2:1: usb_set_interface failed
[83997.410147] 2:2:1: usb_set_interface failed
[83997.410225] 2:2:1: usb_set_interface failed
[83997.410302] 2:2:1: usb_set_interface failed
[83997.410420] 2:1:1: usb_set_interface failed
[83997.410500] 2:1:1: usb_set_interface failed
[83997.410590] 2:1:1: usb_set_interface failed
[83997.410681] 2:1:1: usb_set_interface failed
[83997.410754] 2:1:1: usb_set_interface failed
[83997.410815] 2:1:1: usb_set_interface failed
[83997.410878] 2:1:1: usb_set_interface failed
[83997.410947] 2:1:1: usb_set_interface failed
[83997.411023] 2:1:1: usb_set_interface failed
[83997.411105] 2:1:1: usb_set_interface failed
[83997.411174] 2:1:1: usb_set_interface failed
[83997.411237] 2:1:1: usb_set_interface failed
[83997.411309] 2:1:1: usb_set_interface failed
[83997.411375] 2:1:1: usb_set_interface failed
[83997.411446] 2:1:1: usb_set_interface failed
[83997.411523] 2:1:1: usb_set_interface failed
[83997.411604] 2:1:1: usb_set_interface failed
[83997.411693] 2:2:1: usb_set_interface failed
[83997.411775] 2:2:1: usb_set_interface failed
[83997.411861] 2:2:1: usb_set_interface failed
[83997.411953] 2:2:1: usb_set_interface failed
[83997.412047] 2:2:1: usb_set_interface failed
[83997.412109] 2:2:1: usb_set_interface failed
[83997.412173] 2:2:1: usb_set_interface failed
[83997.412242] 2:2:1: usb_set_interface failed
[83997.412318] 2:2:1: usb_set_interface failed
[83997.412400] 2:2:1: usb_set_interface failed
[83997.412470] 2:2:1: usb_set_interface failed
[83997.412533] 2:2:1: usb_set_interface failed
[83997.412608] 2:2:1: usb_set_interface failed
[83997.412676] 2:2:1: usb_set_interface failed
[83997.412746] 2:2:1: usb_set_interface failed
[83997.412824] 2:2:1: usb_set_interface failed
[83997.420124] 2:2:1: usb_set_interface failed
[83997.420326] 2:1:1: usb_set_interface failed
[83997.420410] 2:1:1: usb_set_interface failed
[83997.420496] 2:1:1: usb_set_interface failed
[83997.420592] 2:1:1: usb_set_interface failed
[83997.420665] 2:1:1: usb_set_interface failed
[83997.420726] 2:1:1: usb_set_interface failed
[83997.420789] 2:1:1: usb_set_interface failed
[83997.420855] 2:1:1: usb_set_interface failed
[83997.420929] 2:1:1: usb_set_interface failed
[83997.421011] 2:1:1: usb_set_interface failed
[83997.421079] 2:1:1: usb_set_interface failed
[83997.421142] 2:1:1: usb_set_interface failed
[83997.421213] 2:1:1: usb_set_interface failed
[83997.421279] 2:1:1: usb_set_interface failed
[83997.421349] 2:1:1: usb_set_interface failed
[83997.421426] 2:1:1: usb_set_interface failed
[83997.421504] 2:1:1: usb_set_interface failed
[83997.421597] 2:2:1: usb_set_interface failed
[83997.421678] 2:2:1: usb_set_interface failed
[83997.421764] 2:2:1: usb_set_interface failed
[83997.421855] 2:2:1: usb_set_interface failed
[83997.421928] 2:2:1: usb_set_interface failed
[83997.421989] 2:2:1: usb_set_interface failed
[83997.422053] 2:2:1: usb_set_interface failed
[83997.422120] 2:2:1: usb_set_interface failed
[83997.422194] 2:2:1: usb_set_interface failed
[83997.422277] 2:2:1: usb_set_interface failed
[83997.422346] 2:2:1: usb_set_interface failed
[83997.422408] 2:2:1: usb_set_interface failed
[83997.422481] 2:2:1: usb_set_interface failed
[83997.422547] 2:2:1: usb_set_interface failed
[83997.422621] 2:2:1: usb_set_interface failed
[83997.422699] 2:2:1: usb_set_interface failed
[83997.422777] 2:2:1: usb_set_interface failed
[83997.422889] 2:1:1: usb_set_interface failed
[83997.422970] 2:1:1: usb_set_interface failed
[83997.423055] 2:1:1: usb_set_interface failed
[83997.423151] 2:1:1: usb_set_interface failed
[83997.445191] 2:1:1: usb_set_interface failed
[83997.445268] 2:1:1: usb_set_interface failed
[83997.445334] 2:1:1: usb_set_interface failed
[83997.445406] 2:1:1: usb_set_interface failed
[83997.445480] 2:1:1: usb_set_interface failed
[83997.445561] 2:1:1: usb_set_interface failed
[83997.445632] 2:1:1: usb_set_interface failed
[83997.445693] 2:1:1: usb_set_interface failed
[83997.445764] 2:1:1: usb_set_interface failed
[83997.445828] 2:1:1: usb_set_interface failed
[83997.445896] 2:1:1: usb_set_interface failed
[83997.445972] 2:1:1: usb_set_interface failed
[83997.446050] 2:1:1: usb_set_interface failed
[83997.446162] 2:2:1: usb_set_interface failed
[83997.446243] 2:2:1: usb_set_interface failed
[83997.446329] 2:2:1: usb_set_interface failed
[83997.446420] 2:2:1: usb_set_interface failed
[83997.446493] 2:2:1: usb_set_interface failed
[83997.446554] 2:2:1: usb_set_interface failed
[83997.446621] 2:2:1: usb_set_interface failed
[83997.446690] 2:2:1: usb_set_interface failed
[83997.446766] 2:2:1: usb_set_interface failed
[83997.446848] 2:2:1: usb_set_interface failed
[83997.446917] 2:2:1: usb_set_interface failed
[83997.446980] 2:2:1: usb_set_interface failed
[83997.447052] 2:2:1: usb_set_interface failed
[83997.447118] 2:2:1: usb_set_interface failed
[83997.447189] 2:2:1: usb_set_interface failed
[83997.447266] 2:2:1: usb_set_interface failed
[83997.447343] 2:2:1: usb_set_interface failed
[83997.620891] 2:1:1: usb_set_interface failed
[83997.620981] 2:1:1: usb_set_interface failed
[83997.621066] 2:1:1: usb_set_interface failed
[83997.621154] 2:1:1: usb_set_interface failed
[83997.621225] 2:1:1: usb_set_interface failed
[83997.621283] 2:1:1: usb_set_interface failed
[83997.621345] 2:1:1: usb_set_interface failed
[83997.621411] 2:1:1: usb_set_interface failed
[83997.621486] 2:1:1: usb_set_interface failed
[83997.621567] 2:1:1: usb_set_interface failed
[83997.621639] 2:1:1: usb_set_interface failed
[83997.621700] 2:1:1: usb_set_interface failed
[83997.621771] 2:1:1: usb_set_interface failed
[83997.621837] 2:1:1: usb_set_interface failed
[83997.621906] 2:1:1: usb_set_interface failed
[83997.621985] 2:1:1: usb_set_interface failed
[83997.622065] 2:1:1: usb_set_interface failed
[83997.622158] 2:2:1: usb_set_interface failed
[83997.622240] 2:2:1: usb_set_interface failed
[83997.622339] 2:2:1: usb_set_interface failed
[83997.622429] 2:2:1: usb_set_interface failed
[83997.622501] 2:2:1: usb_set_interface failed
[83997.622562] 2:2:1: usb_set_interface failed
[83997.622629] 2:2:1: usb_set_interface failed
[83997.622697] 2:2:1: usb_set_interface failed
[83997.622774] 2:2:1: usb_set_interface failed
[83997.622857] 2:2:1: usb_set_interface failed
[83997.622926] 2:2:1: usb_set_interface failed
[83997.622988] 2:2:1: usb_set_interface failed
[83997.623061] 2:2:1: usb_set_interface failed
[83997.623130] 2:2:1: usb_set_interface failed
[83997.623201] 2:2:1: usb_set_interface failed
[83997.623281] 2:2:1: usb_set_interface failed
[83997.623362] 2:2:1: usb_set_interface failed
[83997.623511] 2:1:1: usb_set_interface failed
[83997.623597] 2:1:1: usb_set_interface failed
[83997.623682] 2:1:1: usb_set_interface failed
[83997.623772] 2:1:1: usb_set_interface failed
[83997.623843] 2:1:1: usb_set_interface failed
[83997.623903] 2:1:1: usb_set_interface failed
[83997.623966] 2:1:1: usb_set_interface failed
[83997.624061] 2:1:1: usb_set_interface failed
[83997.626210] 2:1:1: usb_set_interface failed
[83997.626342] 2:1:1: usb_set_interface failed
[83997.626411] 2:1:1: usb_set_interface failed
[83997.626473] 2:1:1: usb_set_interface failed
[83997.626545] 2:1:1: usb_set_interface failed
[83997.626616] 2:1:1: usb_set_interface failed
[83997.626686] 2:1:1: usb_set_interface failed
[83997.626766] 2:1:1: usb_set_interface failed
[83997.626848] 2:1:1: usb_set_interface failed
[83997.626967] 2:2:1: usb_set_interface failed
[83997.627049] 2:2:1: usb_set_interface failed
[83997.627133] 2:2:1: usb_set_interface failed
[83997.627223] 2:2:1: usb_set_interface failed
[83997.627296] 2:2:1: usb_set_interface failed
[83997.627357] 2:2:1: usb_set_interface failed
[83997.627420] 2:2:1: usb_set_interface failed
[83997.627488] 2:2:1: usb_set_interface failed
[83997.627565] 2:2:1: usb_set_interface failed
[83997.627652] 2:2:1: usb_set_interface failed
[83997.627721] 2:2:1: usb_set_interface failed
[83997.627783] 2:2:1: usb_set_interface failed
[83997.627856] 2:2:1: usb_set_interface failed
[83997.627924] 2:2:1: usb_set_interface failed
[83997.628027] 2:2:1: usb_set_interface failed
[83997.628108] 2:2:1: usb_set_interface failed
[83997.628189] 2:2:1: usb_set_interface failed
[83997.628341] 2:1:1: usb_set_interface failed
[83997.628423] 2:1:1: usb_set_interface failed
[83997.628507] 2:1:1: usb_set_interface failed
[83997.628601] 2:1:1: usb_set_interface failed
[83997.628673] 2:1:1: usb_set_interface failed
[83997.628732] 2:1:1: usb_set_interface failed
[83997.628795] 2:1:1: usb_set_interface failed
[83997.628863] 2:1:1: usb_set_interface failed
[83997.628939] 2:1:1: usb_set_interface failed
[83997.629023] 2:1:1: usb_set_interface failed
[83997.629091] 2:1:1: usb_set_interface failed
[83997.629167] 2:1:1: usb_set_interface failed
[83997.629240] 2:1:1: usb_set_interface failed
[83997.629308] 2:1:1: usb_set_interface failed
[83997.629378] 2:1:1: usb_set_interface failed
[83997.629458] 2:1:1: usb_set_interface failed
[83997.629538] 2:1:1: usb_set_interface failed
[83997.629661] 2:2:1: usb_set_interface failed
[83997.629744] 2:2:1: usb_set_interface failed
[83997.629829] 2:2:1: usb_set_interface failed
[83997.629919] 2:2:1: usb_set_interface failed
[83997.629991] 2:2:1: usb_set_interface failed
[83997.630052] 2:2:1: usb_set_interface failed
[83997.630116] 2:2:1: usb_set_interface failed
[83997.630185] 2:2:1: usb_set_interface failed
[83997.630261] 2:2:1: usb_set_interface failed
[83997.630345] 2:2:1: usb_set_interface failed
[83997.630414] 2:2:1: usb_set_interface failed
[83997.630477] 2:2:1: usb_set_interface failed
[83997.630550] 2:2:1: usb_set_interface failed
[83997.630622] 2:2:1: usb_set_interface failed
[83997.630694] 2:2:1: usb_set_interface failed
[83997.630774] 2:2:1: usb_set_interface failed
[83997.630855] 2:2:1: usb_set_interface failed
[83997.630973] 2:1:1: usb_set_interface failed
[83997.631055] 2:1:1: usb_set_interface failed
[83997.631140] 2:1:1: usb_set_interface failed
[83997.631230] 2:1:1: usb_set_interface failed
[83997.631301] 2:1:1: usb_set_interface failed
[83997.631361] 2:1:1: usb_set_interface failed
[83997.631424] 2:1:1: usb_set_interface failed
[83997.631491] 2:1:1: usb_set_interface failed
[83997.631567] 2:1:1: usb_set_interface failed
[83997.631655] 2:1:1: usb_set_interface failed
[83997.631722] 2:1:1: usb_set_interface failed
[83997.631784] 2:1:1: usb_set_interface failed
[83997.631857] 2:1:1: usb_set_interface failed
[83997.631925] 2:1:1: usb_set_interface failed
[83997.632018] 2:1:1: usb_set_interface failed
[83997.632098] 2:1:1: usb_set_interface failed
[83997.632178] 2:1:1: usb_set_interface failed
[83997.632269] 2:2:1: usb_set_interface failed
[83997.632351] 2:2:1: usb_set_interface failed
[83997.632435] 2:2:1: usb_set_interface failed
[83997.632525] 2:2:1: usb_set_interface failed
[83997.632600] 2:2:1: usb_set_interface failed
[83997.632661] 2:2:1: usb_set_interface failed
[83997.632725] 2:2:1: usb_set_interface failed
[83997.632793] 2:2:1: usb_set_interface failed
[83997.632871] 2:2:1: usb_set_interface failed
[83997.632955] 2:2:1: usb_set_interface failed
[83997.633023] 2:2:1: usb_set_interface failed
[83997.634379] 2:2:1: usb_set_interface failed
[83997.634466] 2:2:1: usb_set_interface failed
[83997.634535] 2:2:1: usb_set_interface failed
[83997.634611] 2:2:1: usb_set_interface failed
[83997.634796] 2:2:1: usb_set_interface failed
[83997.634879] 2:2:1: usb_set_interface failed
[83997.635055] 2:1:1: usb_set_interface failed
[83997.635138] 2:1:1: usb_set_interface failed
[83997.635223] 2:1:1: usb_set_interface failed
[83997.635315] 2:1:1: usb_set_interface failed
[83997.635387] 2:1:1: usb_set_interface failed
[83997.635448] 2:1:1: usb_set_interface failed
[83997.635511] 2:1:1: usb_set_interface failed
[83997.635583] 2:1:1: usb_set_interface failed
[83997.635661] 2:1:1: usb_set_interface failed
[83997.635745] 2:1:1: usb_set_interface failed
[83997.635814] 2:1:1: usb_set_interface failed
[83997.635877] 2:1:1: usb_set_interface failed
[83997.635950] 2:1:1: usb_set_interface failed
[83997.636047] 2:1:1: usb_set_interface failed
[83997.636118] 2:1:1: usb_set_interface failed
[83997.636199] 2:1:1: usb_set_interface failed
[83997.636280] 2:1:1: usb_set_interface failed
[83997.636373] 2:2:1: usb_set_interface failed
[83997.636455] 2:2:1: usb_set_interface failed
[83997.636540] 2:2:1: usb_set_interface failed
[83997.636634] 2:2:1: usb_set_interface failed
[83997.636707] 2:2:1: usb_set_interface failed
[83997.636769] 2:2:1: usb_set_interface failed
[83997.636833] 2:2:1: usb_set_interface failed
[83997.636902] 2:2:1: usb_set_interface failed
[83997.636979] 2:2:1: usb_set_interface failed
[83997.637064] 2:2:1: usb_set_interface failed
[83997.637133] 2:2:1: usb_set_interface failed
[83997.637196] 2:2:1: usb_set_interface failed
[83997.637269] 2:2:1: usb_set_interface failed
[83997.637338] 2:2:1: usb_set_interface failed
[83997.637410] 2:2:1: usb_set_interface failed
[83997.637490] 2:2:1: usb_set_interface failed
[83997.637571] 2:2:1: usb_set_interface failed

```

---

### Post by 5BallJuggler on 2009-01-07
> **5BallJuggler said:**
> 

also, I think it may be causing a hardware conflict somewhere, some of my hard drives have become unmountable until i go into windows and shut them down manually.



OK, i've seen the shutdown fault again, here is the display

```

* Shutting down ALSA
* warning 'alsactl store' failed with error message 'alsactl: get_control:262:Cannor read control '2,0,0,Mic Playback Switch,0' :Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
amixer:mixerhw:0 load error: Invalid argument
                                        [COLOR="Red"]FAIL[/COLOR]
```

---

### Post by 5BallJuggler on 2009-01-07
This is the output when running USBView with the headset connected

```
Microsoft LifeChat LX-3000 
Speed: 12Mb/s (full)
USB Version:  1.10
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 045e
Product Id: 070f
Revision Number:  1.00

Config Number: 1
	Number of Interfaces: 4
	Attributes: a0
	MaxPower Needed: 100mA

	Interface Number: 0
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 01
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 1
		Name: snd-usb-audio
		Alternate Number: 1
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 01
			Direction: out
			Attribute: 9
			Type: Isoc
			Max Packet Size: 200
			Interval: 1ms

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 0
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 0

	Interface Number: 2
		Name: snd-usb-audio
		Alternate Number: 1
		Class: 01(audio) 
		Sub Class: 02
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 82
			Direction: in
			Attribute: 5
			Type: Isoc
			Max Packet Size: 100
			Interval: 1ms

	Interface Number: 3
		Name: usbhid
		Alternate Number: 0
		Class: 03(HID  ) 
		Sub Class: 00
		Protocol: 00
		Number of Endpoints: 1

			Endpoint Address: 83
			Direction: in
			Attribute: 3
			Type: Int.
			Max Packet Size: 4
			Interval: 32ms
```

---

### Post by 5BallJuggler on 2009-01-08
This is the output from /proc/bus/usb/devices:-

```
T:  Bus=01 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=045e ProdID=070f Rev= 1.00
S:  Product=Microsoft LifeChat LX-3000
C:* #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:* If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=01(O) Atr=09(Isoc) MxPS= 200 Ivl=1ms
I:* If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=82(I) Atr=05(Isoc) MxPS= 100 Ivl=1ms
I:* If#= 3 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=   4 Ivl=32ms

```

---

### Post by 5BallJuggler on 2009-01-09
```
phil@phil-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA25 [EDIROL UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
phil@phil-desktop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA25 [EDIROL UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by 5BallJuggler on 2009-01-09
I've just noticed something a bit strange, 

When I turn the computer on the sound that accompanies Ubuntu is played through the speakers on my system,
When I log out the notification sound plays through the Headset

Please help, I don't know what to try next,

How do i determine the differences between log in and log out scripts?

---

### Post by markbuntu on 2009-01-09
Well, it seems your headset is sort of working. The problem is that you are having difficulty controlling it. Go here and follow the directions:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

This will give you some tools to see what is going on and get control. If you need more extensive help you can go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am assuming that you are using Hardy 8.04 or Intrepid 8.10.

Once you get that figured out, if virtual box still does not work it might be a permissions problem in the virtual box setup preventing client access to usb or sound devices.

---

### Post by 5BallJuggler on 2009-01-11
> **markbuntu said:**
> Well, it seems your headset is sort of working. The problem is that you are having difficulty controlling it. Go here and follow the directions:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

This will give you some tools to see what is going on and get control. If you need more extensive help you can go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am assuming that you are using Hardy 8.04 or Intrepid 8.10.

Once you get that figured out, if virtual box still does not work it might be a permissions problem in the virtual box setup preventing client access to usb or sound devices.

I've been away for the weekend, and only had chance to look through teh 1st link (which has been a great help. Thanks)

I'm still having an issue with the Device crashing the system though, i'm gonna work through the 2nd link and hope that this sorts it all out.

any further help would be greatly appreciated.

oh yeah, i'm running Ubuntu 8.10

---

