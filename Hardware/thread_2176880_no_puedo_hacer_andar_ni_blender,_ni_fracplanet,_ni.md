---
title: "no puedo hacer andar ni blender, ni fracplanet, ni wings3d en ubuntu"
date: 2013-09-26
forum: Hardware
---

### Post by majo3 on 2013-09-26
Holaaa gente!! soy nueva en el este foro y dando mis primeros pasos con UBUNTU, les cuento que no me andan los programas con 3d, intenté por terminal, y uno de ellos, Wings3d, me dice esto:  wings3d
Trying OpenGL modes
  [{buffer_size,32},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,0},{accum_size,16}]
  [{buffer_size,16},{depth_size,24},{stencil_size,8},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,8},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,0},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,0},{accum_size,0}]
  [{buffer_size,15},{depth_size,16},{stencil_size,8},{accum_size,16}]
  [{buffer_size,15},{depth_size,16},{stencil_size,0},{accum_size,16}]
  [{buffer_size,15},{depth_size,16},{stencil_size,0},{accum_size,0}]
  [{buffer_size,0},{depth_size,0},{stencil_size,0},{accum_size,0}]

###########################################

Failed to find any suitable OpenGL mode.

Make sure that OpenGL drivers are installed.


###########################################


Retrying with multisampling disabled.
Trying OpenGL modes
  [{buffer_size,32},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,32},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,8},{accum_size,16}]
  [{buffer_size,24},{depth_size,24},{stencil_size,0},{accum_size,16}]
  [{buffer_size,16},{depth_size,24},{stencil_size,8},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,8},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,0},{accum_size,16}]
  [{buffer_size,16},{depth_size,16},{stencil_size,0},{accum_size,0}]
  [{buffer_size,15},{depth_size,16},{stencil_size,8},{accum_size,16}]
  [{buffer_size,15},{depth_size,16},{stencil_size,0},{accum_size,16}]
  [{buffer_size,15},{depth_size,16},{stencil_size,0},{accum_size,0}]
  [{buffer_size,0},{depth_size,0},{stencil_size,0},{accum_size,0}]

###########################################

Failed to find any suitable OpenGL mode.

Make sure that OpenGL drivers are installed.


###########################################


=ERROR REPORT==== 26-Sep-2013::12:00:26 ===
Error in process <0.30.0> with exit value: {"No suitable OpenGL mode found (are OpenGL drivers installed?)",[{wings_init,video_mode_failure,0},{wings_init,init,0},{wings,init,1}]}



Fatal internal error - log written to /home/majo/wings_crash.dump

por fis, cualquier aporte es agradecido,  quiero aprender y poder hacer andar el 3d!!!

---

### Post by gmunioz on 2013-09-26
¿Qué tarjeta gráfica tienes?
Lo averiguas ejecutando en una terminal:
> sudo su
lspci | grep -i vga 
Esta es una salida para nvidia:
> 00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)

¿Tienes activa la aceleración de gráficos?
Para determinar si tu equipo soporta aceleración de gráficos ejecutaen una terminal:
> sudo su
apt-get install mesa-utils
glxinfo | grep -i render 
Esta es una salida para nvidia con aceleración activa:
> OpenGL renderer string: GeForce 7025 / nForce 630a/integrated/SSE2/3DNOW!
GL_KTX_buffer_region, GL_NVX_conditional_render,
GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
Si el equipo no soporta aceleración gráfica o no tienes los drivers con ella activa, los programas no funcionaran.

---

