# prepare filenames for ffmpeg input
for line in `ls | awk '{printf "%04d ", NR; print $0}'`; do ln -s `echo $line | cut -d ' ' -f 2` N`echo $line | cut -d ' ' -f 1`.JPG; done

# LG webOS compatible
ffmpeg -r 50 -i N%04d.JPG -vcodec libx265 -pix_fmt yuv420p -vf scale=out_color_matrix=bt709:h=2160:w=-2
