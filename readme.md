# Environment(the same as Llava code)
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip  # enable PEP 660 support
pip install -e .
pip install -e ".[train]"
pip install flash-attn --no-build-isolation

# Dataset
image data should be organized as follow:

|---coco

|     |---train2017  /lustre/scratch/shared-folders/vision-project/Code/jinhong.wang/llava1.5_llama2/data/llava_finetune_data/coco/train2017

|     |---val2017  /lustre/scratch/shared-folders/vision-project/Datasets/MSCoco_245k/val2017
|---gqa

|     |---images   /lustre/scratch/shared-folders/vision-project/Code/jinhong.wang/llava1.5_llama2/data/llava_finetune_data/gqa/images

|---ocr_vqa

|     |---images   /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/ocrvqa/ocrvqa
|---textvqa

|     |---train_images  /lustre/scratch/shared-folders/vision-project/Code/jinhong.wang/llava1.5_llama2/data/llava_finetune_data/textvqa/train_images

|---vg

|     |---VG_100K  /lustre/scratch/shared-folders/vision-project/Datasets/VisualGenome_100k/VG_100K

|     |---VG_100K_2  /lustre/scratch/shared-folders/vision-project/Datasets/VisualGenome_100k/VG_100K_2

|---vg_total   (for lrv)  /lustre/scratch/shared-folders/vision-project/Datasets/VisualGenome_100k/vg_total

|---chart_lrv  (for chart in lrv)  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/LRVinstruction/chart_image

|---MIMIC-IT   (for MIMIC-IT)

|     |---MIMIC-IT-Release

|     |     |---CGD

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/CGD/images

|     |     |---DC

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/DC/images

|     |     |---E4D

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/E4D/images

|     |     |---LA

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/LA/images

|     |     |---SD

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/SD/images

|     |     |---SN

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/SN/images

|     |     |---TVC

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/TVC/images

|     |     |---VST

|     |     |     |---images  /lustre/scratch/shared-folders/vision-project/Tuning_Datasets/MIMIC_IT/MIMIC-IT-Release/VST/images


# Finetune model

bash scripts/v1_5/finetune.sh

tips: data path and model path should be modified in "scripts/v1_5/finetune.sh"

# Evaluate model 

Evaluate on MME benchmark: bash scripts/v1_5/eval/mme.sh

Evaluate on POPE benchmark: bash scripts/v1_5/eval/pope.sh

tips: also need to modify the model path and data path

