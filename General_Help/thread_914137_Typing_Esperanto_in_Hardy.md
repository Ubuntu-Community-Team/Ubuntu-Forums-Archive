---
title: "Typing Esperanto in Hardy"
date: 2008-09-08
forum: General Help
---

### Post by brallan on 2008-09-08
Look below to viranaso's post for the current solution...
*********************************************
Those making the switch from windows and the excellent freeware Ek! (Esperanta Klavaro) which is NOT available for linux may wish to use the x-method to type esperanto characters (&#265;&#285;&#309;&#349;&#365;) using cx, gx, sx, ux, etc. 

This is an update of the [instructions on the google code website,]("http://code.google.com/p/iksilo/wiki/INSTALL_en")

Those wishing to get the non-ascii esperanto characters to work in Ubuntu 8.04, should consider using SCIM, the Smart Common Input Method. Although the default esperanto keyboard in ubuntu 8.04 is quite easy to add -

System > Preferences > Keyboard # Layout > Add

- this keyboard is difficult to use for multilingual work, as you have to switch out of the keyboard every time you wish to type q, y x, or w. As most urls begin with www, I far prefer SCIM rather than having to change keyboards constantly. it also combines well with dvorak, and multiple keyboard in the keyboard preferences. With a few rare exceptions - eg: to type "linux", one must type  double x - "linuxx", else it will appear as "lin&#365;" - In this sense, SCIM behaves exactly as does Ek!

**_To install SCIM for use with Esperanto characters:_**

open a terminal window and type the following to install scim, the panel applet, character maps, and dependencies:

```
sudo apt-get update
sudo apt-get install scim scim-m17n m17n-db m17n-contrib scim-bridge-agent scim-bridge-client-gtk  scim-bridge-client-qt scim-bridge-client-qt4
```then
[LIST]
[*]Start SCIM with the command scim. ({Alt+F2} scim {Enter})
[/LIST]

[LIST]
[*]Right-click the icon of SCIM (which shows a keyboard and can be found in the system tray).
[/LIST]

[LIST]
[*]Select SCIM Setup
[/LIST]

[LIST]
[*]Go to IMEngine > Global Setup
[/LIST]

[LIST]
[*]Click Disable All    (this is to save systemn resources)
[/LIST]

[LIST]
[*]Scroll down to Other and select eo-x-sistemo or another eo layout to your liking.
[/LIST]

[LIST]
[*]Click Apply and OK
[/LIST]

[LIST]
[*]Reboot your system, or only the graphical system (X). ({Ctrl+Alt+Backspace})
[/LIST]

Try whether it works

[LIST]
[*]Start the program in which you want to type.
[/LIST]

[LIST]
[*]Click on the icon of SCIM (which shows a keyboard and can be found in the system tray)
[/LIST]

[LIST]
[*]Select an inputmethod, ion this case eo-x-sistemo, in the menu Other. (You can switch it on and off afterwards with {Ctrl+Space})
[/LIST]

[LIST]
[*]Type "E&#293;o&#349;an&#285;o &#265;iu&#309;a&#365;de" (Ehxosxangxo cxiujxauxde) to try whether the Esperanto letters work.
[/LIST]

If it doesn't work, reboot the computer or the graphical system again ({Ctrl+Alt+Backspace}), and try again.

---

### Post by brallan on 2008-09-08
Por tiuj kiuj volas havi &#265;apelilon, bonan simplan iksilon por ubuntu, mi rekomendas SCIM, (the Smart Common Input Method) tiun kiu oni kutimas uzi por &#265;inaj, japanaj, literoj, ktp. Ek! estas senkosta liberkoda esperanta klavaro en windows, sed &#285;i ne haveblas por linukso. Do, &#265;i tie mi montros la formon povi tajpi (&#265;&#285;&#309;&#349;&#365;) per cx, gx, sx, ux, ktp. 

Mi trovis tiujn &#265;i instrukciojn en [ the google code pa&#285;aro,]("http://code.google.com/p/iksilo/wiki/INSTALL_en")

Kvankam estas tre facila havi esperantan klavaron en Ubuntu 8.04:

Sistemo > Preferoj > Klavaro # Tajpiloj > Aldonu

La klavaro estas malfacila uzi por plurlingvaj laboroj, a&#365; e&#265; por povi tajpi yahoo a&#365; retpo&#349;tadresoj kiuj enhavas q, y x, a&#365; w. Pro tio mi multe preferas uzi SCIM anstata&#365; konstante &#349;an&#285;i klavaron. &#284;i anka&#365; bone uzi&#285;as kun dvorak,a&#365; ajna klavaro en la klavaraj preferoj. Krom malmultaj kromkazoj - ekz tajpi "linux", oni devas tajpi dufoje ikson - "linuxx", sene &#285;i aperos kiel "lin&#365;" - Tiel SCIM tutsame agas kiel Ek! Alia problemo estas ke [bitcimo]("https://bugs.launchpad.net/ubuntu/+bug/225055/comments/8") malebligas ke tiu klavaro da&#365;re funkcios post reeko de komputilo.

Do, mi rekomendas:

**_&#264;apelitaj literoj per instalado de SCIM:_**

Por instal SCIM, la panelprogrameto, klavaroj kaj &#265;iuj dependa&#309;oj, malfermu terminalfenestro kaj tajpi la sekvan:

```
sudo apt-get update
sudo apt-get install scim scim-m17n m17n-db m17n-contrib scim-bridge-agent scim-bridge-client-gtk  scim-bridge-client-qt scim-bridge-client-qt4
```

kaj poste:
[LIST]
[*]ekigu SCIM. ({Alt+F2} scim {Enter})
[/LIST]

[LIST]
[*]Dekstre klaku la ikonon de SCIM (kiu montras klavaron kaj trovi&#285;as en sistempanelo).
[/LIST]

[LIST]
[*]Elektu SCIM Setup
[/LIST]

[LIST]
[*]Iru al IMEngine > Global Setup
[/LIST]

[LIST]
[*]Klaku Disable All    (por &#349;pari sistem-memoron)
[/LIST]

[LIST]
[*]Subigu al Other kaj elektu eo-x-sistemo a&#365; alia eo aran&#285;o kiu vin pla&#265;as.
[/LIST]

[LIST]
[*]Klaku Apply kaj OK
[/LIST]
[LIST]
[*]Rekomencigu vian komputilon, a&#365; nur la x-grafiksistemon ({Ctrl+Alt+Backspace})
[/LIST]

Provu &#265;u funkciis:

[LIST]
[*]Eku la programon en kiu vi volas tajpi.
[/LIST]

[LIST]
[*]Elektu la ikonon de SCIM  (kiu montras klavaron kaj trovi&#285;as en sistempanelo)
[/LIST]

[LIST]
[*]Elektu enirmetodo, &#265;ikaze eo-x-sistemo, en la menuo Other. (vi poste povos ekkomenci &#285;in per {Ctrl+Space})
[/LIST]

[LIST]
[*]Tajpu "E&#293;o&#349;an&#285;o &#265;iu&#309;a&#365;de" (Ehxosxangxo cxiujxauxde) por vidi &#265;u &#265;apelitaj literoj funkcias.
[/LIST]

Se ne funkcias, reeku la komputilon a&#365; la grafiksistemon.({Ctrl+Alt+Backspace}), kaj reprovu.

---

### Post by brallan on 2010-03-04
It seems as if SCIM is no longer working for Karmic, and that there are no longer any team members working on development.... 

[http://www.scim-im.org/](http://www.scim-im.org/)
[http://sourceforge.net/apps/mediawiki/scim/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/scim/index.php?title=Main_Page)
 
These instructions no longer seem to work, and I'm wondering if tweaking some of the internals of SCIM are necessary to get it to work. Anyone have any luck?

---

### Post by brallan on 2010-03-04
&#348;ajnas ke SCIM jam ne funkcias por KARMIC, kaj ke mankas kunlaborantoj en la pluprogramado....

[http://www.scim-im.org/](http://www.scim-im.org/)
[http://sourceforge.net/apps/mediawik...itle=Main_Page]("http://sourceforge.net/apps/mediawiki/scim/index.php?title=Main_Page")
 
Do, la supraj instrukcioj jam ne validas, kaj mi scivolas &#265;u iel &#349;an&#285;i interna&#309;ojn de la SCIMprogramo iel helpus. &#264;u iu sukcesis?

---

### Post by viranaso on 2010-04-15
It is now (as of Karmic) much easier to configure Ubuntu (Kubuntu) to facilitate typing the accented Esperanto letters. This is explained at [http://eo.openoffice.org/eo_kaj_ooo.html]("http://eo.openoffice.org/eo_kaj_ooo.html").

In Gnome, select menu "System", "Preferences", "Keyboard". Chose tab "Layouts" and the desired layout, e.g. "USA". Click on the button "Layout Options" and "Adding Esperanto circumflexes (supersigno)". Choose one of the three options, e.g. "To the corresponding key in a Qwerty keyboard", then "Key to choose 3rd level" and then select they keys you want to use as special keys, for example "Left Win". To finish click "Close"and "Close".

---

### Post by viranaso on 2010-04-15
Ek de 2009 en Linukso por tajpi la &#265;apelitajn literojn estas e&#265; pli konvene ol anta&#365;e. Oni povas simple aldoni la klavojn por la &#265;apelitaj literoj al sia kutima aran&#285;o per la menuo Sistemo. 

Legu la detalojn por Gnome kaj KDE &#265;e [http://eo.openoffice.org/eo_kaj_ooo.html]("http://eo.openoffice.org/eo_kaj_ooo.html")

---

### Post by Monkus on 2010-11-10
I usually work on a Mac, and I have it setup to use the x-system to write Esperanto. Is there anyway that I can write Esperanto using the x-system in Ubuntu? I prefer that method and would like to keep doing it that way. Thanks.

---

### Post by brallan on 2010-11-11
> **Monkus said:**
> I usually work on a Mac, and I have it setup to use the x-system to write Esperanto. Is there anyway that I can write Esperanto using the x-system in Ubuntu? I prefer that method and would like to keep doing it that way. Thanks.

[CENTER]ENGISH BELOW....
[/CENTER]
Monkus, la unua metodo kiun mi rakontis (per SCIM) eble funkcias ankora&#365;, &#265;u vi jam provis &#285;in?

Mi anka&#365; &#349;atis na ek!, kaj neniam mi kontenti&#285;is de la solvo de nuresperanta klavaro.  La ubuntu eoklavaro ne permesas uzi tre utilajn literojn "q", "w", "x" kaj "y". Kiel oni povas skribi retadreson se mankas la w?

Sed finfine mi ekalkutimi&#285;is la solvon kiun atentigis viranaso, kaj uzas na dekstra Alt, kiun mi jam uzadas por fari na &#8364; kaj aliajn signojn. Do, kiam mi premas na dekstra ALT CSGHJU mi ricevas &#264;&#348;&#284;&#292;&#308;&#364;. Beda&#365;rinde en la hispana klavaro &#285;i legi&#285;as kiel §©&#330;&#294;J&#8593;.
===================================
Monkus, the first method I described (with SCIM) may still work, have you tried it yet?

I liked ek! as well, as I was never happy with the esperanto keyboard. I was always frustrated by the lack of the very useful letters  "q", "w", "x" kaj "y". How do you type a URL without w?

but eventually I moved over to the soution which viranaso pointed out, using the right Alt key, which I had already gotten used to in order to make &#8364; and other symbols. Thus, by pressing ALT CSGHJU with the native english keyboard I get &#264;&#348;&#284;&#292;&#308;&#364;. Unfortunately with the Spanish keyboard I get §©&#330;&#294;J&#8593;.

---

### Post by Monkus on 2010-11-17
brallan, Thanks for your reply. Yes, I did try the SCIM method, but unfortunately it did not work for me. If you have any other ideas, I'm open to try. I'll just have to type regular x-sistemo for now.

---

### Post by brallan on 2010-11-21
> **Monkus said:**
> brallan, Thanks for your reply. Yes, I did try the SCIM method, but unfortunately it did not work for me. If you have any other ideas, I'm open to try. I'll just have to type regular x-sistemo for now.

Well it would be nice to find a solution to that annoyance, but I doubt  that you will find one without siting down and writing it yourself or  going personally to the SCIM programmers and asking them or paying them  to help you. The source code is there and a solution worked, it  shouldn't be too hard to get it working again. The solution as it stands  (I am using the right ALT key) is quite simple and elegant, it seems  that your resistance to it is that it is not the one you have gotten  used to in windows, and if you are doing a lot of switching back and  forth between operating systems, that is indeed annoying. 

But have a look at other distros. The native solution to ubuntu may not  be availabe to other distros, and the x-solution may have been the way  around it.

Good Luck!

Do, estus bele se iu trovus solvon al tiu &#285;eno, sed mi dubas ke la  problemo solvi&#285;os se vi ne mem &#285;in kodigas a&#365; persone petas a&#365; pagas al  la programistoj de SCIM funkciigi tion. Haveblas la fontkodo kaj la  solvo ja funkciis, ne devas esti tre kompika funkciigi &#285;in denove. La  solvo kiu ekzistas (mi estas uzante la dekstran ALT klavon) estas simpla  kaj bela, &#349;ajnas ke via rezistemo venas pro tio ke vi jam kutimi&#285;is al  la Windows-solvo, kaj se vi ofte &#349;an&#285;as inter operaciujoj, ja &#285;enas. 

Sed rigardu en aliaj lokoj, eble la solvo kiu ekzistas en Ubuntu ne  funkcias en alia distro, kaj eble ili havas iks-solvon a&#365; iksilon. 

Bon&#349;ancon!

---

