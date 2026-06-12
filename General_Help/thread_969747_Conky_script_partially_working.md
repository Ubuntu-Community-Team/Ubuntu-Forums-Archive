---
title: "Conky script partially working"
date: 2008-11-03
forum: General Help
---

### Post by rusty_jones on 2008-11-03
This is my conky file and amarok script;
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
${font openlogos:size=20}  ${font Arial:size=20}${color Tan1}UBUNTU 8.10    ${color Ivory}LINUX ${font openlogos:size=20}
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

${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}
External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}
${font Arial:bold:size=10}${color Tan2}WEATHER ${color DarkSlateGray}${hr 2}
${font}${color DimGray}
${voffset -25}${font Weather:size=45}${execi 1800 conkyForecast –location=USPA0008 –datatype=WF}
${alignc 22}${voffset -60}${font Arial:bold:size=10}${color DimGray}${execi 1800 conkyForecast –location=USPA0008 –datatype=HT}
$font${voffset -55}${alignr}${color white}Wind: ${execi 1800 conkyForecast –location=USPA0008 –datatype=WS}
${alignr}${color white}Humidity: ${execi 1800 conkyForecast –location=USPA0008 –datatype=HM}
${alignr}${color white}Precipitation: ${execi 1800 conkyForecast –location=USPA0008 –datatype=PC}
${color white}Sunrise: $alignr${execi 1800 conkyForecast –location=USPA0008 –datatype=SR}${alignr}
Sunset: $alignr${execi 1800 conkyForecast –location=USPA0008 –datatype=SS}$color

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

```
#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

# Collection Info
totalArtists)      dcop amarok collection totalArtists ;;
totalAlbums)       dcop amarok collection totalAlbums ;;
totalTracks)       dcop amarok collection totalTracks ;;
totalGenres)       dcop amarok collection totalGenres ;;
totalCompilations) dcop amarok collection totalCompilations ;;

# Collection Stats
most_songs_by_artist) dcop amarok collection query 'SELECT t1.name FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_by_artist_n) dcop amarok collection query 'SELECT count(t2.artist) FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_are_genre) dcop amarok collection query 'SELECT t1.name FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_are_genre_n) dcop amarok collection query 'SELECT count(t2.genre) FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_during_year) dcop amarok collection query 'SELECT t1.name FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_songs_during_year_n) dcop amarok collection query 'SELECT count(t2.year) FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_albums_by_artist) dcop amarok collection query 'SELECT name FROM artist WHERE id=(SELECT t1.artist from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1);' ;;
most_albums_by_artist_n) dcop amarok collection query 'SELECT count(artist) from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1;' ;;
most_albums_are_genre) dcop amarok collection query 'SELECT name FROM genre WHERE id=(SELECT t1.genre from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1);' ;;
most_albums_are_genre_n) dcop amarok collection query 'SELECT count(genre) from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1;' ;;
most_albums_during_year) dcop amarok collection query 'SELECT name FROM year WHERE id=(SELECT t1.year from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1);' ;;
most_albums_during_year_n) dcop amarok collection query 'SELECT count(year) from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1;' ;;

esac


```

Everything works fine in the script with the exception of the Now Playing and Collection Info and Stats does not populate. Would anyone know what's wrong?

PS. yes I have the mysql database setup.


Rusty

---

