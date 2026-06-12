---
title: "USB2 HDD, showing full when half empty."
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by Beej on 2005-08-04
Hi I wonder if anyone can help, I have a Cowon Iaudio M3L 20GB which works just like a USB2 HDD. I have been happily using Goobox to rip my CD's to my Home folder and then simply drag them onto the iaudio HDD icon on my desktop.

Last time I tried to add music i got amessage telling me the device is full. One problem with this there is only 7.8 GB on it, showing only 20MB free. Has anybody got any idea what the problem might be? 

Thanks,

Beej.

---

### Post by varunus on 2005-08-04
Weird...

Open up a terminal and cd over to the USB hard drive (first type "cd /media" and then type cd "mountpoint", you can use the "ls" commands to list your mounted devices, it'll be fairly obvious which one is the HD).  Then, type the following:
```
sudo du . -h
```

What is the output of that?

---

### Post by Beej on 2005-08-04
output is

16K     ./record
16K     ./playlist
16K     ./TEXTFILE
16K     ./_SYS
1.1G    ./.Trash-ben/Marco's tunes
67M     ./.Trash-ben/Korn/Life Is Peachy
96M     ./.Trash-ben/Korn/Follow The Leader
162M    ./.Trash-ben/Korn
1.2G    ./.Trash-ben
16K     ./System Volume Information
16K     ./voice
16K     ./firmware
80K     ./system
96K     ./Recycled
100M    ./All Music/Devin Townsend/Terria
62M     ./All Music/Devin Townsend/Physicist
161M    ./All Music/Devin Townsend
41M     ./All Music/Deicide/Once Upon The Cross
41M     ./All Music/Deicide
102M    ./All Music/Deftones/Adrenaline
68M     ./All Music/Deftones/White Pony
170M    ./All Music/Deftones
85M     ./All Music/Daft Punk/Discovery
63M     ./All Music/Daft Punk/Human After All
147M    ./All Music/Daft Punk
97M     ./All Music/Cypress Hill/iv
78M     ./All Music/Cypress Hill/III (Temples of Boom)
61M     ./All Music/Cypress Hill/Black Sunday
234M    ./All Music/Cypress Hill
92M     ./All Music/Boards of Canada/Geogaddi
92M     ./All Music/Boards of Canada
16K     ./All Music/Basement Jaxx/Kish Kash
71M     ./All Music/Basement Jaxx
42M     ./All Music/Audioslave
47M     ./All Music/Aphex Twin/Come to Daddy
47M     ./All Music/Aphex Twin
78M     ./All Music/Alter Ego
47M     ./All Music/Air/Premier Symptomes
47M     ./All Music/Air
70M     ./All Music/2 Many DJ's/as heard on Radio Soulwax Pt.2
70M     ./All Music/2 Many DJ's
83M     ./All Music/Lemon Jelly/Lost Horizons
83M     ./All Music/Lemon Jelly
97M     ./All Music/Leftfield/Leftism
97M     ./All Music/Leftfield
72M     ./All Music/Kyuss/Sky Valley
100M    ./All Music/Kyuss/And The Circus Leaves Town
171M    ./All Music/Kyuss
87M     ./All Music/Kosheen - Resist
52M     ./All Music/Kings of Leon/Aha Shake Heartbreak
53M     ./All Music/Kings of Leon
90M     ./All Music/Gorillaz - Gorillaz
60M     ./All Music/Goldfrapp/Black Cherry
400M    ./All Music/Goldfrapp/Felt Mountain
460M    ./All Music/Goldfrapp
80M     ./All Music/Fun Lovin' Criminals/Come Find Yourself
72M     ./All Music/Fun Lovin' Criminals/100% Columbian
151M    ./All Music/Fun Lovin' Criminals
41M     ./All Music/Fu Manchu/Start the Machine
42M     ./All Music/Fu Manchu
48M     ./All Music/Downset/Downset
48M     ./All Music/Downset
25M     ./All Music/Dillinger Escape Plan/Irony Is A Dead Scene
56M     ./All Music/Dillinger Escape Plan/Miss Machine
81M     ./All Music/Dillinger Escape Plan
77M     ./All Music/Die Krupps/Paradise Now
77M     ./All Music/Die Krupps
58M     ./All Music/Royksopp/Melody A.M
58M     ./All Music/Royksopp
100M    ./All Music/Roni Size/Newforms
100M    ./All Music/Roni Size
63M     ./All Music/Rammstein/Mutter
67M     ./All Music/Rammstein/Reise, Reise
129M    ./All Music/Rammstein
63M     ./All Music/Rage Against The Machine/The Battle for Los Angeles
65M     ./All Music/Rage Against The Machine/Evil Empire
73M     ./All Music/Rage Against The Machine/Rage Against The Machine
200M    ./All Music/Rage Against The Machine
86M     ./All Music/Queens of the Stone Age/Songs for the Deaf
65M     ./All Music/Queens of the Stone Age/Queens of the Stone Age
59M     ./All Music/Queens of the Stone Age/Rated R
87M     ./All Music/Queens of the Stone Age/Lullabies tp Paralyze
295M    ./All Music/Queens of the Stone Age
95M     ./All Music/Propellerheads/Decksanddrumsandrockandroll
95M     ./All Music/Propellerheads
122M    ./All Music/Probot/Aponymous
122M    ./All Music/Probot
69M     ./All Music/Portishead/Dummy
69M     ./All Music/Portishead
56M     ./All Music/Nine Inch Nails/Fixed
68M     ./All Music/Nine Inch Nails/The Fragile/Right
76M     ./All Music/Nine Inch Nails/The Fragile/Left
144M    ./All Music/Nine Inch Nails/The Fragile
90M     ./All Music/Nine Inch Nails/The Downward Spiral
89M     ./All Music/Nine Inch Nails/With Teeth
71M     ./All Music/Nine Inch Nails/things falling apart
60M     ./All Music/Nine Inch Nails/And All That Could Have Been - Disc 2 (halo seventeen)
102M    ./All Music/Nine Inch Nails/And All That Could Have Been (cd1) [Halo Seventeen]
48M     ./All Music/Nine Inch Nails/The Perfect Drug Versions (halo eleven)
658M    ./All Music/Nine Inch Nails
48K     ./All Music/Morcheeba
84M     ./All Music/Monster Magnet/Powertrip
84M     ./All Music/Monster Magnet
85M     ./All Music/Moloko/Things To Make And Do
85M     ./All Music/Moloko
65M     ./All Music/Mastodon/Leviathan
63M     ./All Music/Mastodon/Remission
128M    ./All Music/Mastodon
95M     ./All Music/Mudvayne/L.D. 50
95M     ./All Music/Mudvayne
82M     ./All Music/Zero 7/When It Falls
85M     ./All Music/Zero 7/Simple Things
166M    ./All Music/Zero 7
72M     ./All Music/White Zombie/Astro - Creep 2000
80M     ./All Music/White Zombie/La Secorcisto, Devil Music Vol. 1
152M    ./All Music/White Zombie
66M     ./All Music/The Workhorse Movement/Sons of Pioneers
66M     ./All Music/The Workhorse Movement
84M     ./All Music/The Chemical Brothers/Push the Button
82M     ./All Music/The Chemical Brothers/Surrender
69M     ./All Music/The Chemical Brothers/Exit Planet Dust
25M     ./All Music/The Chemical Brothers/Dig Your Own Hole
76M     ./All Music/The Chemical Brothers/Come With Us
333M    ./All Music/The Chemical Brothers
63M     ./All Music/Pist.On/Number One
63M     ./All Music/Pist.On
50M     ./All Music/Rob Zombie/Hellbilly Deluxe
50M     ./All Music/Rob Zombie
33M     ./All Music/Scissor Sisters/Scissor Sisters
33M     ./All Music/Scissor Sisters
16K     ./All Music/Sepultura/Chaos A. D
82M     ./All Music/Sepultura/arise (remasters)
82M     ./All Music/Sepultura
92M     ./All Music/Slipknot/Iowa
92M     ./All Music/Slipknot/Slipknot
183M    ./All Music/Slipknot
85M     ./All Music/Type O Negative/Life Is Killing Me
62M     ./All Music/Type O Negative/Life Is Killing Me (Bonus CD)
100M    ./All Music/Type O Negative/World_Coming_Down
246M    ./All Music/Type O Negative
96M     ./All Music/Mr_Scruff_Presents_Keep_It_Solid_Steel_Vol.1
101M    ./All Music/High Contrast/High Society
101M    ./All Music/High Contrast
77M     ./All Music/Fear Factory/Demanufacture
77M     ./All Music/Fear Factory
98M     ./All Music/Bob Sinclair/Enjoy (The Movie & The Mix) Disc 1
98M     ./All Music/Bob Sinclair
67M     ./All Music/A_Perfect_Circle/Mer_de_Noms
67M     ./All Music/A_Perfect_Circle
63M     ./All Music/Talking Heads/Little Creatures
103M    ./All Music/Talking Heads/Stop Making Sense (Special New Edition)
73M     ./All Music/Talking Heads/Naked
238M    ./All Music/Talking Heads
80M     ./All Music/One Minute Silence/Buy Now...Saved Later
80M     ./All Music/One Minute Silence
61M     ./All Music/Foo Fighters/Foo Fighters
61M     ./All Music/Foo Fighters
108M    ./All Music/The Prodigy/Music For The Jilted Generation
78M     ./All Music/The Prodigy/The Fat Of The Land
186M    ./All Music/The Prodigy
69M     ./All Music/Machine Head/The Burning Red
69M     ./All Music/Machine Head
35M     ./All Music/Korn/Life Is Peachy
96M     ./All Music/Korn/Follow The Leader
130M    ./All Music/Korn
94M     ./All Music/Iron Maiden/Dance Of Death
61M     ./All Music/Iron Maiden/Seventh Son Of A Seventh Son
155M    ./All Music/Iron Maiden
62M     ./All Music/Red Hot Chili Peppers/Mother's Milk
102M    ./All Music/Red Hot Chili Peppers/Blood Sugar Sex Magik
164M    ./All Music/Red Hot Chili Peppers
67M     ./All Music/Megadeth/The System Has Failed
57M     ./All Music/Megadeth/Rust in peace
123M    ./All Music/Megadeth
7.6G    ./All Music
62M     ./Red Hot Chili Peppers/Mother's Milk
62M     ./Red Hot Chili Peppers
8.9G    .

---

### Post by varunus on 2005-08-05
That's really weird.  Is the player partitioned or something?  If so, you may need to mount its second partition or something...but that doesn't make any sense.  I've used a 60 GB ipod with no problems on Ubuntu, I have no idea why its not working for you...try google, I guess.  Maybe there's something you need to do to enable large hard drives...

---

### Post by Beej on 2005-08-06
No, no partition. The drive is fat32, I've just checked it on my parents windows machine and it reads the size of the drive at 18.6 G with 10 G free.

I'm a little confused about whats going on, but I'm pretty new to Linux I'm sure I'll figure it out.

Thanks for the help,

Beej.

---

### Post by varunus on 2005-08-06
Yeah, I haven't seen a problem like this one before...

Try booting KNOPPIX from a CD or the Ubuntu LiveCD, if you have access to either of those.  Then plug in your player.  Does that show the size correctly?

---

### Post by Beej on 2005-08-08
Downloaded Knoppix live cd and ran that, comes up with exactly the same value for free space.  ](*,) 

I wonder if its a specific problem to the player although from  googling "iAudio M3 problems" and having a read I haven't found anybody with the same issue.

Its not a big problem currently but it will be the next time I go CD shopping!

---

### Post by wyopistachio on 2006-09-01
I had a similar problem with a USB mp3 player, perhaps you can "fix" it the way I did.  Exploring to the player in Windows I found a .trash file that I never saw in Kubuntu.  Deleting it in windows gave me back the room on the player in Kubuntu.

Now I just need to know how to do that in Kubuntu.  (what I was searching for when I found this thread)

---

