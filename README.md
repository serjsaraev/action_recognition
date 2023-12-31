# Topic 5. Action Recognition

## Состав команды

1. Сергей Сараев
2. Надежда Кондратьева
3. Кирилл Зарубин

## Установка окружения

Установка окружения осуществляется с помощью Anaconda следующей командой:
```angular2html
conda activate myenv
conda env update --file enviroment.yml --prune
```
## Данные

В качестве обучающего датасета использовался датасет Kinetics 2020-700, из которого были выбрани видео, содержащие в названии лейбла
слово 'dancing'. Всего классов получилось 15. Были выбраны сэмплы для train и validation выборки по 100 и 10 экземпляров на класс соответственно. Для скачивания видео был реализован код с помощью библиотеки yt-dlp. 


## Эксперименты

Весь код и все эксперименты находятся в ноутбуке action_recognition-hw.ipynb

### Были проведены следующие эксперименты

- Обучение модели EfficientNet v2 на одном случайном кадре из видео.
- Обучение модели ResNet-152 на последовательности видео с аугментацией для train датасета.
- Обучение видеотрансформера VideoMAE последовательности видео с аугментацией для train датасета.
- Двустадийное обучение видеотрансформера VideoMAE, преобученного на датасете  Kinetics с 400 классами. На первом этапе обучается только последний слой классификатора моедли, далее размораживаются остальные веса.
- Обучение EfficientNet на сэмпле кадров из видео

## Метрики
В качестве целевой метрики была выбрана accuracy ввиду сбалансированности классов.

## Итоговые результаты экспериментов

| Model                                  | val_accuracy | train_loss | valid_loss |
|----------------------------------------|--------------|------------|------------|
| EfficientNet v2 на одном кадре         | 0.258        | 1.62       | 2.596      | 
| ResNet-152                             | 0.375        | 2.25       | 1.2        | 
| VideoMAE с обычными весами             | 0.073        | 2.68       | 2.67       | 
| Двустадийное обучение видеотрансформера VideoMAE | 0.747        | 0.484      | 0.855 | 
| Обучение EfficientNet на сэмпле кадров (8) с усреднением ответа | 0.072 | 2.769 | 2.814|
