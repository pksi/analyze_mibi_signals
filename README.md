# analyze_mibi_signals
Download the data file (75MB) from:
https://storage.googleapis.com/mibiscope-share/InterviewTaskData.h5
The downloaded file contains mass spectrometry data from rastering over a 512x512 grid. The raster
goes across each row from left to right, starting with the top row and repeating this left-to-right pattern
until it reaches the bottom. At each pixel in the grid, two types of data are collected: a series of
timestamps and their corresponding ion counts.
If you choose to complete this task using Python, you can import the PyTables library to read the sample
data. (You may use another language if you prefer, but will need to figure out how to read this HDF5 file in
that language.) In Python, to access the timestamps and counts from pixel i in the grid, where i is in the
range [0, 512*512) , you could use:
import tables
with tables.open_file('data.h5') as infile:
timestamps = infile.root.time[i]
counts = infile.root.counts[i]
Here, timestamps and counts are each an array of length d , where counts[k] is the number of ions
that arrived at time timestamps[k] .
We know at what timestamps certain types of ions should arrive. In particular,
- Red ions arrive with timestamps between 16029 and 16078
- Green ions arrive with timestamps between12118 and 12184
- Blue ions arrive with timestamps between 15829 and 15879
- Gray ions arrive with timestamps between 6315 and 6876
Tasks:
1. Create a grayscale image showing the distribution of gray ions. The goal is to visually
demonstrate the relative amounts of the gray channel across the grid, so that a person can
intuitively see where there are a lot of gray ions vs. where there are few.
2. Create an RGB image showing the red, green and blue ions.
3. Are the blue ions more likely to occur near the red ions or near the green ions?
