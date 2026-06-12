---
title: "Why are all entries in Celsius"
date: 2008-11-04
forum: General Help
---

### Post by rusty_jones on 2008-11-04
Why are all my entries coming back in Celsius?
I am new to linux and would appreciate any help that you can give.
 

```
${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=USPA0311 –datatype=WF}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=USPA0311 –datatype=HT}
$font${voffset -55}${alignr}${color White}Wind: ${execi 1800 conkyForecast –location=USPA0311 –datatype=WS}
${alignr}${color White}Humidity: ${execi 1800 conkyForecast –location=USPA0311 –datatype=HM}
${alignr}${color White}Precipitation: ${execi 1800 conkyForecast –location=USPA0311 –datatype=PC}

${color White}Sunrise: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SR}${alignr}
Sunset: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SS}$color

```

Thanks in advance,

Rusty

---

### Post by abrussak on 2008-11-04
place --i on each for imperial measures

---

### Post by ad_267 on 2008-11-04
But can you get them in Kelvin?

---

### Post by rusty_jones on 2008-11-04
what do you mean place --i on each for imperial measures.

I don't know anything about these scripts.

---

### Post by ad_267 on 2008-11-04
I think it should be --imperial or -i with a single dash. It's like this:

```
${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=WF --imperial}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=HT --imperial}
$font${voffset -55}${alignr}${color White}Wind: ${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=WS --imperial}
${alignr}${color White}Humidity: ${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=HM --imperial}
${alignr}${color White}Precipitation: ${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=PC --imperial}

${color White}Sunrise: $alignr${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=SR --imperial}${alignr}
Sunset: $alignr${execi 1800 conkyForecast &#8211;location=USPA0311 &#8211;datatype=SS --imperial}$color
```

---

### Post by rusty_jones on 2008-11-04
I guess i did not explain myself well enough. All the entries are all returning F entries from the script from above. 

Sunrise = 48F
Sunset  = 48F
So does WIND, Humidity and Precipitation.

Rusty

---

### Post by lisati on 2008-11-04
> **rusty_jones said:**
> I guess i did not explain myself well enough. All the entries are all returning F entries from the script from above. 

Sunrise = 48F
Sunset  = 48F
So does WIND, Humidity and Precipitation.

Rusty

No idea of what's happening: I usually measure sunrise in a.m., and sunset in p.m., not celsius or farhenheit (or Kelvin)

---

### Post by ad_267 on 2008-11-04
Ok so that has nothing to do with the temperatures being in Celsius.

Have you done this:
> For a working script you NEED to define, in a user specific config file, a partner id and registration code for the weather.com xoap service. For this purpose the config file should be copied to "~/.conkyForecast.config" and setup as required.


as described here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)


What do you get if you go to Applications - Accessories - Terminal and enter:
```
conkyForecast &#8211;location=USPA0311 &#8211;datatype=WS --enableerrors
```

---

### Post by rusty_jones on 2008-11-04
[HTML]ERROR: Unable to load locale 'USPA0311' [Errno 2] No translation file found for domain: 'conkyForecast'[/HTML]

I tried the the code from above and got the error.
I checked the conkyforcast.config and the locale , partner ID and license key are all filled in. Any other avenues that I can check?

Rusty

---

### Post by ad_267 on 2008-11-04
I haven't used this before but just doing a search for that error gives me these pages:

[http://ubuntuforums.org/showthread.php?t=869328&page=58](http://ubuntuforums.org/showthread.php?t=869328&page=58)
[http://ph.ubuntuforums.com/showthread.php?p=6008881](http://ph.ubuntuforums.com/showthread.php?p=6008881)
[http://ubuntuforums.org/showthread.php?t=869328&page=58](http://ubuntuforums.org/showthread.php?t=869328&page=58)

It sounds like your configuration file is probably wrong. The locale should be your language, i.e. "en".

---

### Post by rusty_jones on 2008-11-04
Everything still the same.


> # config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = en 
XOAP_PARTNER_ID = aaaaaaaaaa 
XOAP_LICENCE_KEY = aaaaaaaaaaa 

This is my complete conkyrc file maybe someone can find the problem.

Thanks to all for helping out!!!!!

Rusty

```
# Conky configuration
    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 300 5
    maximum_width 500
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT
${font openlogos:size=15}  ${font Arial:size=15}${color Tan1}  UBUNTU 8.10  ${color Ivory}LINUX ${font openlogos:size=15}
${font Arial:bold:size=10}${color Tan1}TIME ${color DarkSlateGray}${hr 2}
${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}




${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
${font Arial:bold:size=10}${color Tan1}PROCESSOR ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU  ${cpu}% ${cpubar cpu}
${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
${fs_bar /media/disk}
${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color White}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %
$font${top_mem name 6}${alignr}${top mem 6} %
$font${top_mem name 7}${alignr}${top mem 7} %
$font${top_mem name 8}${alignr}${top mem 8} %
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color White}IP on eth0 $alignr ${addr eth0}
External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=USPA0311 –datatype=WF --imperial}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=USPA0311 –datatype=HT --imperial}
$font${voffset -55}${alignr}${color White}Wind: ${execi 1800 conkyForecast –location=USPA0311 –datatype=WS --imperial}
${alignr}${color White}Humidity: ${execi 1800 conkyForecast –location=USPA0311 –datatype=HM --imperial}
${alignr}${color White}Precipitation: ${execi 1800 conkyForecast –location=USPA0311 –datatype=PC --imperial}

${color White}Sunrise: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SR --imperial}${alignr}
Sunset: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SS --imperial}$color


${font Arial:bold:size=10}${color Tan1}MUSIC${color DarkSlateGray} ${hr 2}
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif# Conky configuration
    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 300 5
    maximum_width 500
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT
${font openlogos:size=15}  ${font Arial:size=15}${color Tan1}  UBUNTU 8.10  ${color Ivory}LINUX ${font openlogos:size=15}
${font Arial:bold:size=10}${color Tan1}TIME ${color DarkSlateGray}${hr 2}
${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}




${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
${font Arial:bold:size=10}${color Tan1}PROCESSOR ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU  ${cpu}% ${cpubar cpu}
${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
${fs_bar /media/disk}
${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color White}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %
$font${top_mem name 6}${alignr}${top mem 6} %
$font${top_mem name 7}${alignr}${top mem 7} %
$font${top_mem name 8}${alignr}${top mem 8} %
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color White}IP on eth0 $alignr ${addr eth0}
External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=USPA0311 –datatype=WF --imperial}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=USPA0311 –datatype=HT --imperial}
$font${voffset -55}${alignr}${color White}Wind: ${execi 1800 conkyForecast –location=USPA0311 –datatype=WS --imperial}
${alignr}${color White}Humidity: ${execi 1800 conkyForecast –location=USPA0311 –datatype=HM --imperial}
${alignr}${color White}Precipitation: ${execi 1800 conkyForecast –location=USPA0311 –datatype=PC --imperial}

${color White}Sunrise: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SR --imperial}${alignr}
Sunset: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SS --imperial}$color


${font Arial:bold:size=10}${color Tan1}MUSIC${color DarkSlateGray} ${hr 2}
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif# Conky configuration
    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 300 5
    maximum_width 500
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 10
    gap_y 10
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    use_spacer yes
    text_buffer_size 256

    TEXT
${font openlogos:size=15}  ${font Arial:size=15}${color Tan1}  UBUNTU 8.10  ${color Ivory}LINUX ${font openlogos:size=15}
${font Arial:bold:size=10}${color Tan1}TIME ${color DarkSlateGray}${hr 2}
${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}




${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
${font Arial:bold:size=10}${color Tan1}PROCESSOR ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU  ${cpu}% ${cpubar cpu}
${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/disk $alignc ${fs_used /media/disk} / ${fs_size /media/disk} $alignr ${fs_free_perc /media/disk}%
${fs_bar /media/disk}
${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color White}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %
$font${top_mem name 6}${alignr}${top mem 6} %
$font${top_mem name 7}${alignr}${top mem 7} %
$font${top_mem name 8}${alignr}${top mem 8} %
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color White}IP on eth0 $alignr ${addr eth0}
External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}

${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=USPA0311 –datatype=WF --imperial}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=USPA0311 –datatype=HT --imperial}
$font${voffset -55}${alignr}${color White}Wind: ${execi 1800 conkyForecast –location=USPA0311 –datatype=WS --imperial}
${alignr}${color White}Humidity: ${execi 1800 conkyForecast –location=USPA0311 –datatype=HM --imperial}
${alignr}${color White}Precipitation: ${execi 1800 conkyForecast –location=USPA0311 –datatype=PC --imperial}

${color White}Sunrise: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SR --imperial}${alignr}
Sunset: $alignr${execi 1800 conkyForecast –location=USPA0311 –datatype=SS --imperial}$color


${font Arial:bold:size=10}${color Tan1}MUSIC${color DarkSlateGray} ${hr 2}
$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif
```

This is my complete conkyrc file maybe someone can find the problem.

Thanks to all for helping out!!!!!

Rusty

---

### Post by ad_267 on 2008-11-04
I suggest you ask in this thread which was started by the guy that develops the weather script: [http://ubuntuforums.org/showthread.php?t=869328&page=74](http://ubuntuforums.org/showthread.php?t=869328&page=74)

You'll probably get a lot faster response from somebody who knows what they're talking about.

---

### Post by rusty_jones on 2008-11-04
Thanks


Rusty

---

