# Time Series Exercise 7: Spectral Analysis, Spectral Density and Time-Invariant Linear Filters

## Name: SRINATH N

## Roll No: 2305003009

## Department: AIML

## AIM

To simulate a time series, calculate its spectral density, perform spectral analysis using the periodogram, and study the effect of a time-invariant linear filter.

## PROGRAM

### Python Code

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Generate a time series
n = 600
t = np.arange(n)

x = (
    np.sin(2 * np.pi * 0.01 * t)
    + 0.8 * np.sin(2 * np.pi * 0.35 * t)
    + 0.2 * np.random.randn(n)
)

# Calculate spectral density using periodogram
frequency, power = signal.periodogram(x)

# Find dominant frequency
dominant_freq = frequency[np.argmax(power)]

print("Dominant Frequency:", dominant_freq)

# Apply a 15-point moving average filter
window = 15
filtered = np.convolve(
    x,
    np.ones(window) / window,
    mode="same"
)

# Calculate periodograms before and after filtering
f1, p1 = signal.periodogram(x)
f2, p2 = signal.periodogram(filtered)

# Plot time-domain and frequency-domain analysis
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.plot(t, x, label="Original", alpha=0.7)
plt.plot(t, filtered, label="15-pt Filtered", linewidth=2)
plt.title("Time Domain Analysis")
plt.xlabel("Time")
plt.ylabel("Amplitude")
plt.legend()

plt.subplot(1, 2, 2)
plt.plot(f1, p1, label="Original Spectrum", alpha=0.7)
plt.plot(f2, p2, label="Filtered Spectrum", linewidth=2)
plt.title("Frequency Domain Analysis")
plt.xlabel("Frequency")
plt.ylabel("Power Spectral Density")
plt.legend()

plt.tight_layout()
plt.show()
```

## OUTPUT
<img width="940" height="420" alt="image" src="https://github.com/user-attachments/assets/6f8674d1-f71b-4b70-a554-45f17d4e0b7b" />


## RESULT

Thus, the time series was successfully simulated, its spectral density was calculated using the periodogram, and the effect of a time-invariant moving average filter was studied through time-domain and frequency-domain analysis.
