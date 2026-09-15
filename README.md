# 🎹 AudioMind AI — Neural Music Generation Workstation

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.16%2B%20%2F%20Keras%203-orange.svg?logo=tensorflow&logoColor=white)](https://tensorflow.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B.svg?logo=streamlit&logoColor=white)](https://streamlit.io/)


**AudioMind AI** is an end-to-end deep learning project designed to learn, model, and compose polyphonic musical arrangements. Built using Python, Keras/TensorFlow, and `music21`, the system processes raw MIDI datasets, encodes notes and chords into symbolic sequences, trains a recurrent Long Short-Term Memory (LSTM) network, and delivers an interactive studio interface powered by Streamlit and Magenta.js.

---

## 📸 Key Features

- **Symbolic Music Processing:** Parses pitches, durations, and polyphonic chords from raw `.mid` files using `music21`.
- **Recurrent Deep Learning Core:** Multi-layer LSTM network with Dropout layers to prevent overfitting on sequential chord progressions.
- **Studio Console UI:** Sleek, glassmorphism-styled workstation featuring interactive controls, sidebar navigation, and session render logs.
- **Sampling Hyperparameters:** Fine-tune creativity (Softmax Temperature), output note length, and playback tempo (BPM) on the fly.
- **Client-Side SoundFont Playback:** Integrates `@magenta/music` for instant browser-based Web Audio synthesis—no DAW or local software synth required.
- **Dynamic Piano Roll Display:** Renders synchronized visual note pitch ribbons alongside an active playback playhead.
- **Universal MIDI Export:** Download industry-standard `.mid` output files ready for production inside any digital audio workstation (FL Studio, Ableton, Logic, GarageBand).

---

## 📂 Project Structure

```text
AudioMind AI/
├── dataset/
│   └── midi/                  # Place training .mid/.midi files here
├── models/
│   ├── notes.pkl              # Serialized note/chord vocabulary mapping
│   └── music_lstm.keras       # Trained Keras model artifact
├── src/
│   ├── preprocess.py          # Extracts note/chord tokens from dataset
│   ├── train.py               # Prepares sequence windows & trains LSTM
│   └── generate.py            # Generates new sequences from seed notes
├── generated/
│   └── generated_music.mid    # Latest composition output
├── app.py                     # Streamlit Studio workstation interface
├── requirements.txt           # Environment dependencies
└── README.md

## 🛠️ Tech Stack
Machine Learning & Modeling: TensorFlow / Keras 3, NumPy

Music Information Retrieval (MIR): music21

Web Frontend: Streamlit, HTML5 Web Audio API, @magenta/music

Audio Output: Standard MIDI (Type 0 / Type 1)


Parameter,Range,Description
Creativity (Temperature),0.2 – 1.3,"Controls randomness in the Softmax probability distribution. Lower values (<0.5) produce structured, repetitive harmonies; higher values (>0.8) create jazzier, experimental note jumps."
Note Count,50 – 500,Total number of musical events/notes generated in the piece.
Tempo (BPM),60 – 160,Playback speed metadata injected into the sequence timeline.
Harmonic Key,Presets,Scales and harmonic target ranges for the composition.

🚀 Getting Started
1. Clone the Repository & Set Up Environment
Bash
git clone [https://github.com/your-username/AudioMind-AI.git](https://github.com/your-username/AudioMind-AI.git)
cd AudioMind-AI

# Create and activate virtual environment
python -m venv venv
# On Windows PowerShell:
.\venv\Scripts\Activate.ps1
# On Linux/macOS:
source venv/bin/activate
2. Install Dependencies
Bash
pip install -r requirements.txt
(If creating requirements.txt, include: tensorflow, keras, music21, streamlit, numpy)

🎵 Step-by-Step Workflow
Step 1: Add Training MIDI Files
Place clean, single-track or partitioned multi-track .mid files into the dataset folder:

Bash
dataset/midi/
  ├── classical1.mid
  ├── piano1.mid
  └── sonata2.mid
Step 2: Preprocess the Dataset
Parse musical notes and chords into a serialized vocabulary cache:

Bash
python src/preprocess.py
Output: models/notes.pkl

Step 3: Train the LSTM Model
Train the recurrent neural network on sequence windows (e.g., 64 or 100 notes per sequence):

Bash
python src/train.py
Output: models/music_lstm.keras

Step 4: Launch the Studio Console
Run the interactive Streamlit dashboard:

Bash
streamlit run app.py
