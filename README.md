import pygame
import random

# Oyun ekranının boyutları
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600

# Renkler
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
RED = (255, 0, 0)

# Köpek objesi sınıfı
class Dog(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((50, 50))
        self.image.fill(RED)
        self.rect = self.image.get_rect()
        self.rect.center = (SCREEN_WIDTH // 2, SCREEN_HEIGHT // 2)

# Oyun başlatma
pygame.init()

# Ekran oluşturma
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Köpek Oyunu")

# Köpek objesi oluşturma
dog = Dog()

# Köpek grubu
all_sprites = pygame.sprite.Group()
all_sprites.add(dog)

# Oyun döngüsü
running = True
clock = pygame.time.Clock()

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Ekranı temizleme
    screen.fill(WHITE)

    # Köpek objesini güncelleme ve çizme
    all_sprites.update()
    all_sprites.draw(screen)

    # Ekranı güncelleme
    pygame.display.flip()

    # FPS ayarı
    clock.tick(60)

# Oyunu kapatma
pygame.quit()
